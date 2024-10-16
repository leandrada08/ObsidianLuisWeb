# Operador Nabla

## Divergencia
Denotamos la divergencia del campo vectorial A como$$\nabla.A$$
## Rotor
Denotamos el rotor del campor vectorial A como $$\nabla x A$$
## Gradiente
Denotamos el gradiente del vector A como $$\nabla A$$


## Propiedades del operador Nabla
### **Identidades del Operador Nabla**

1. **Gradiente**:  
   $$
   \nabla f = \left( \frac{\partial f}{\partial x}, \frac{\partial f}{\partial y}, \frac{\partial f}{\partial z} \right)
   $$

2. **Divergencia del Gradiente (Laplaciano)**:  
   $$
   \nabla \cdot (\nabla f) = \nabla^2 f
   $$

3. **Rotacional del Gradiente**:  
   $$
   \nabla \times (\nabla f) = 0
   $$

4. **Divergencia del Rotacional**:  
   $$
   \nabla \cdot (\nabla \times \mathbf{A}) = 0
   $$

5. **Rotacional del Rotacional**:  
   $$
   \nabla \times (\nabla \times \mathbf{A}) = \nabla (\nabla \cdot \mathbf{A}) - \nabla^2 \mathbf{A}
   $$

6. **Divergencia del Producto Escalar**:  
   $$
   \nabla \cdot (\psi \mathbf{A}) = \psi (\nabla \cdot \mathbf{A}) + (\nabla \psi) \cdot \mathbf{A}
   $$

7. **Rotacional del Producto Escalar**:  
   $$
   \nabla \times (\psi \mathbf{A}) = \psi (\nabla \times \mathbf{A}) + (\nabla \psi) \times \mathbf{A}
   $$

8. **Laplaciano de un Producto Escalar**:  
   $$
   \nabla^2 (\psi \phi) = \psi \nabla^2 \phi + 2 (\nabla \psi) \cdot (\nabla \phi) + \phi \nabla^2 \psi
   $$

9. **Rotacional del Producto Cruzado**:  
   $$
   \nabla \times (\mathbf{A} \times \mathbf{B}) = (\mathbf{B} \cdot \nabla) \mathbf{A} - (\mathbf{A} \cdot \nabla) \mathbf{B} + \mathbf{A} (\nabla \cdot \mathbf{B}) - \mathbf{B} (\nabla \cdot \mathbf{A})
   $$

10. **Divergencia del Producto Cruzado**:  
   $$
   \nabla \cdot (\mathbf{A} \times \mathbf{B}) = (\nabla \times \mathbf{A}) \cdot \mathbf{B} - \mathbf{A} \cdot (\nabla \times \mathbf{B})
   $$

11. **Gradiente del Producto Escalar de Vectores**:  
   $$
   \nabla (\mathbf{A} \cdot \mathbf{B}) = (\mathbf{A} \cdot \nabla) \mathbf{B} + (\mathbf{B} \cdot \nabla) \mathbf{A} + \mathbf{A} \times (\nabla \times \mathbf{B}) + \mathbf{B} \times (\nabla \times \mathbf{A})
   $$

12. **Laplaciano de un Cociente**:  
   $$
   \nabla^2 \left( \frac{\psi}{\phi} \right) = \frac{\phi \nabla^2 \psi - 2 (\nabla \phi \cdot \nabla \psi) + \psi \nabla^2 \phi}{\phi^2}
   $$
   