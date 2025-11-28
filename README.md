# Gestion-Estudiantes
📚 SGEstudiantes – Sistema de Gestión de Estudiantes

Proyecto de aplicación de escritorio desarrollado en C# (.NET Windows Forms) que permite gestionar estudiantes a nivel académico, aplicando conceptos de Programación Orientada a Objetos y patrones de diseño.

🚀 Funcionalidades principales

✔ Registrar estudiantes
✔ Editar datos existentes
✔ Eliminar estudiantes
✔ Buscar por nombre, identificación o carrera
✔ Visualizar listado en un DataGrid
✔ Diferenciar estudiantes Pregrado y Posgrado

🧰 Tecnologías utilizadas

C# — .NET Framework / .NET WinForms

Programación Orientada a Objetos

Patrón Factory

Patrón Repository

Persistencia en memoria (lista interna)

Sistema modular con formularios

🧠 Arquitectura
SGEstudiantes
 ├─ Models
 │   ├─ Student.cs
 │   ├─ Undergrad.cs
 │   ├─ Postgrad.cs
 ├─ Factories
 │   └─ StudentFactory.cs
 ├─ Repositories
 │   ├─ IStudentRepository.cs
 │   └─ StudentRepository.cs
 ├─ Forms
 │   ├─ MainForm.cs
 │   ├─ FormStudents.cs
 │   └─ FormStudentDetails.cs

🏗️ Modelos
Student (Clase abstracta base)

StudentId

Nombre

Identificacion

Carrera

FechaIngreso

Tipo (abstract)

Undergrad (Hereda de Student)

Semestre

Tipo => "Pregrado"

Postgrad (Hereda de Student)

Programa

Tipo => "Posgrado"

🧪 Patrón Factory

Produce objetos dinámicamente según el tipo seleccionado:

public class StudentFactory
{
    public Student CreateStudent(string tipo)
    {
        return tipo.ToLower() switch
        {
            "pregrado" => new Undergrad(),
            "posgrado" => new Postgrad(),
            _ => null
        };
    }
}

🗃️ Patrón Repository

Centraliza las operaciones:

Obtener

Insertar

Actualizar

Eliminar

📦 Implementación en memoria (sin base de datos), fácil de migrar.

🖥️ Interfaz gráfica

MainForm → Navegación

FormStudents → CRUD + búsqueda

FormStudentDetails → Registro / edición con validación

📦 Base de datos (opcional)

El proyecto funciona en memoria.
Si deseas migrar a SQL Server:

👉 Scripts recomendados:

CREATE TABLE Students (
    StudentId INT IDENTITY(1,1) PRIMARY KEY,
    Nombre NVARCHAR(120) NOT NULL,
    Identificacion NVARCHAR(50) NOT NULL,
    Carrera NVARCHAR(120) NOT NULL,
    FechaIngreso DATE NOT NULL,
    Tipo VARCHAR(20) NOT NULL
);

CREATE TABLE Undergrad (
    StudentId INT PRIMARY KEY,
    Semestre INT NOT NULL,
    FOREIGN KEY (StudentId) REFERENCES Students(StudentId)
);

CREATE TABLE Postgrad (
    StudentId INT PRIMARY KEY,
    Programa NVARCHAR(120) NOT NULL,
    FOREIGN KEY (StudentId) REFERENCES Students(StudentId)
);

📦 Características técnicas destacadas

✔ Herencia para modelar tipos de estudiantes

✔ Encapsulamiento y validaciones

✔ Polimorfismo en renderización

✔ Separación de capas UI / lógica / datos

✔ Código limpio y organizado

🧑‍💻 Autor

Nombre del estudiante
Juan David Galvis Henao
Juan David Urrego Jaramillo
Institución Universitaria Pascual Bravo
Herramientas De Programacion 2
2025
