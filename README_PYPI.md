# TenMiNaTor - Framework de Deep Learning Ultraligero

![TenMiNaTor Logo](https://img.shields.io/badge/TenMiNaTor-v0.1.0-blue)
![Python](https://img.shields.io/badge/Python-3.8%2B-green)
![License](https://img.shields.io/badge/License-MIT-yellow)

**TenMiNaTor** es un framework de Deep Learning inspirado en PyTorch, diseñado específicamente para dispositivos con almacenamiento limitado. Ofrece un motor de autograd completo, soporte multi-backend, y características avanzadas como Nested Learning, Relational Memory y vLLM para inferencia rápida.

---

## 🚀 Instalación

### Instalación desde PyPI (Recomendado)

```bash
pip install tenminator
```

### Instalación desde el Código Fuente

```bash
git clone https://github.com/Men-Bat/tenminator.git
cd tenminator
pip install -e .
```

### Dependencias Opcionales

Para habilitar características avanzadas, instala las dependencias opcionales:

```bash
# Para soporte de JAX (aceleración con JIT)
pip install tenminator[jax]

# Para soporte de CuPy (aceleración GPU)
pip install tenminator[cupy]

# Para soporte de Numba (JIT compilation)
pip install tenminator[numba]

# Para integración con bases de datos
pip install tenminator[database]

# Para todas las características
pip install tenminator[all]
```

---

## 📖 Uso Básico

### 1. Crear un Tensor

```python
from tenminator import Tensor

# Crear tensor con gradientes
x = Tensor([1.0, 2.0, 3.0], requires_grad=True)
y = Tensor([4.0, 5.0, 6.0], requires_grad=True)

# Operaciones
z = x + y
loss = (z ** 2).sum()

# Backpropagation
loss.backward()

print(x.grad)  # Gradientes de x
```

### 2. Construir una Red Neuronal

```python
from tenminator.nn import Module, Linear, ReLU

class SimpleNet(Module):
    def __init__(self):
        super().__init__()
        self.fc1 = Linear(10, 64)
        self.relu = ReLU()
        self.fc2 = Linear(64, 1)
    
    def forward(self, x):
        x = self.fc1(x)
        x = self.relu(x)
        x = self.fc2(x)
        return x

# Crear modelo
model = SimpleNet()
```

### 3. Entrenar un Modelo

```python
from tenminator.optim import Adam
from tenminator.training import TrainingController
import numpy as np

# Datos de ejemplo
X = np.random.randn(100, 10)
y = np.random.randn(100, 1)

# Optimizador
optimizer = Adam(model.parameters(), lr=0.01)

# Controlador de entrenamiento (sistema 10x12)
controller = TrainingController(
    max_iterations=100,
    early_stop_patience=12,
    checkpoint_dir='./checkpoints'
)

# Loop de entrenamiento
for epoch in range(10):
    # Forward pass
    X_tensor = Tensor(X, requires_grad=False)
    y_tensor = Tensor(y, requires_grad=False)
    
    predictions = model(X_tensor)
    loss = ((predictions - y_tensor) ** 2).sum() / len(y)
    
    # Backward pass
    optimizer.zero_grad()
    loss.backward()
    optimizer.step()
    
    print(f"Epoch {epoch+1}, Loss: {loss.data:.6f}")
    
    # Early stopping
    if controller.should_stop(float(loss.data)):
        print("Early stopping triggered!")
        break
```

### 4. Guardar y Cargar Modelos

```python
# Guardar checkpoint
controller.save_checkpoint(
    model=model,
    optimizer=optimizer,
    epoch=epoch,
    loss=float(loss.data)
)

# Cargar checkpoint
checkpoint = controller.load_checkpoint()
if checkpoint:
    model.load_state_dict(checkpoint['model_state'])
    optimizer.load_state_dict(checkpoint['optimizer_state'])
```

---

## 🎯 Características Avanzadas

### Nested Learning

```python
from tenminator.nested import NestedOptimizer

# Optimizador anidado para problemas jerárquicos
nested_opt = NestedOptimizer(
    inner_optimizer=Adam(inner_params, lr=0.01),
    outer_optimizer=Adam(outer_params, lr=0.001),
    inner_steps=5
)
```

### Relational Memory

```python
from tenminator.reasoning import RelationalMemory

# Memoria relacional para aprendizaje con grafos
memory = RelationalMemory(memory_size=100, key_size=64)
memory.store(key, value, relations)
retrieved = memory.retrieve(query)
```

### Multi-Backend Support

```python
from tenminator.backends import set_backend

# Cambiar backend
set_backend('jax')    # Para aceleración con JAX
set_backend('cupy')   # Para GPU con CuPy
set_backend('numba')  # Para JIT con Numba
set_backend('numpy')  # Backend por defecto
```

### Integración con Bases de Datos

```python
from tenminator.data import SQLDataLoader

# Cargar datos desde SQL
loader = SQLDataLoader(
    connection_string='mysql://user:pass@localhost/db',
    query='SELECT * FROM training_data'
)
data = loader.load()
```

---

## 🌐 Uso de la Interfaz Web

TenMiNaTor incluye una interfaz web interactiva para entrenar modelos visualmente:

```bash
# Iniciar servidor web
python -m tenminator.web

# Acceder en: http://localhost:3000
```

### Características de la Interfaz Web:

- **Subida de Archivos**: Sube CSV, JSON o TXT con tus datos
- **Control de Entrenamiento**: Botones de Iniciar/Pausar/Reanudar/Detener
- **Visualización en Tiempo Real**: Ve el progreso del entrenamiento
- **Panel Lateral**: Visualiza código y datos cargados
- **Historial de Sesiones**: Accede a entrenamientos anteriores

---

## 📊 Comandos de CLI

TenMiNaTor incluye una interfaz de línea de comandos:

```bash
# Entrenar un modelo desde CLI
tenminator train --data data.csv --config config.json

# Evaluar un modelo
tenminator evaluate --model checkpoint.pth --data test.csv

# Exportar modelo
tenminator export --model checkpoint.pth --format onnx

# Ver información del sistema
tenminator info
```

---

## 🔧 Configuración

Crea un archivo `config.json` para configurar tu entrenamiento:

```json
{
  "model": {
    "type": "SimpleNet",
    "input_size": 10,
    "hidden_size": 64,
    "output_size": 1
  },
  "training": {
    "epochs": 10,
    "batch_size": 32,
    "learning_rate": 0.01,
    "optimizer": "Adam",
    "early_stop_patience": 12,
    "max_iterations": 100
  },
  "backend": "numpy",
  "checkpoint_dir": "./checkpoints"
}
```

---

## 📚 Documentación Completa

Para documentación completa, visita:

- **Manual de Uso**: [MANUAL_DE_USO.md](https://github.com/tu-usuario/tenminator/blob/main/MANUAL_DE_USO.md)
- **Quickstart**: [QUICKSTART.md](https://github.com/tu-usuario/tenminator/blob/main/QUICKSTART.md)
- **API Reference**: [docs/api.md](https://github.com/tu-usuario/tenminator/blob/main/docs/api.md)

---

## 🤝 Contribuir

¡Las contribuciones son bienvenidas! Por favor:

1. Fork el repositorio
2. Crea una rama para tu feature (`git checkout -b feature/AmazingFeature`)
3. Commit tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abre un Pull Request

---

## 📄 Licencia

Este proyecto está licenciado bajo la Licencia MIT - ver el archivo [LICENSE](LICENSE) para más detalles.

---

## 🙏 Agradecimientos

- Inspirado por PyTorch y TensorFlow Lite
- Construido con NumPy, JAX, Numba y CuPy
- Interfaz web con React y tRPC

---

## 📞 Soporte

- **Issues**: [GitHub Issues](https://github.com/tu-usuario/tenminator/issues)
- **Discusiones**: [GitHub Discussions](https://github.com/tu-usuario/tenminator/discussions)
- **Email**: support@tenminator.dev

---

## 🎓 Ejemplos

Encuentra más ejemplos en el directorio `examples/`:

- `examples/mnist.py` - Clasificación de dígitos MNIST
- `examples/sentiment.py` - Análisis de sentimientos
- `examples/timeseries.py` - Predicción de series temporales
- `examples/reinforcement.py` - Aprendizaje por refuerzo
- `examples/transformer.py` - Modelo Transformer

---

**¡Comienza a entrenar modelos de IA hoy con TenMiNaTor!** 🚀
