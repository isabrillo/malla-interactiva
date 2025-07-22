const cursos = [
  {
    semestre: "Semestre 1",
    ramos: [
      { nombre: "Gestión e Investigación en Salud I", abre: ["Gestión e Investigación en Salud II"] },
      { nombre: "Morfología I", abre: ["Morfología II"] },
      { nombre: "Fundamentos Moleculares de los Procesos Biológicos I", abre: ["Fundamentos Moleculares de los Procesos Biológicos II"] },
      { nombre: "Química" },
      { nombre: "Matemáticas" },
      { nombre: "Introducción a Tecnología Médica" }
    ]
  },
  {
    semestre: "Semestre 2",
    ramos: [
      { nombre: "Gestión e Investigación en Salud II", abre: ["Gestión e Investigación en Salud III"], requiere: ["Gestión e Investigación en Salud I"] },
      { nombre: "Morfología II", abre: ["Fundamentos Biológicos de los Procesos Funcionales, sus Alteraciones y Modulación Farmacológica"], requiere: ["Morfología I"] },
      { nombre: "Fundamentos Moleculares de los Procesos Biológicos II", abre: ["Fundamentos Biológicos de los Procesos Funcionales, sus Alteraciones y Modulación Farmacológica"], requiere: ["Fundamentos Moleculares de los Procesos Biológicos I"] },
      { nombre: "Física General", abre: ["Física Aplicada I"] }
    ]
  },
  {
    semestre: "Semestre 3",
    ramos: [
      { nombre: "Gestión e Investigación en Salud III", abre: ["Gestión e Investigación en Salud IV"], requiere: ["Gestión e Investigación en Salud II"] },
      { nombre: "Electivo" },
      { nombre: "Fundamentos Biológicos de los Procesos Funcionales, sus Alteraciones y Modulación Farmacológica" },
      { nombre: "Principios Fundamentales de Instrumentación", abre: ["Fotografía Médica", "Mantención Equipos Radiológicos"] }
    ]
  },
  {
    semestre: "Semestre IV",
    ramos: [
      { nombre: "Gestión e Investigación en Salud IV", abre: ["Investigación I"], requiere: ["Gestión e Investigación en Salud III"] },
      { nombre: "Módulo Genito Urinario", abre: ["Módulo Integrado Enfermedades Prioritarias y Aspectos Legales"] },
      { nombre: "Física Aplicada I", abre: ["Física Aplicada II"], requiere: ["Física General"] }
    ]
  },
  {
    semestre: "Semestre V",
    ramos: [
      { nombre: "Sistema Digestivo", abre: ["Módulo Integrado Enfermedades Prioritarias y Aspectos Legales"] },
      { nombre: "Anatomía Radiológica I", abre: ["Anatomía Radiológica II"] },
      { nombre: "Técnicas Radiológicas I", abre: ["Técnicas Radiológicas II"] },
      { nombre: "Física Aplicada II", abre: ["Dosimetría y Protección Radiológica"], requiere: ["Física Aplicada I"] }
    ]
  },
  {
    semestre: "Semestre VI",
    ramos: [
      { nombre: "Sistema Cardiovascular", abre: ["Módulo Integrado Enfermedades Prioritarias y Aspectos Legales"] },
      { nombre: "Investigación I", abre: ["Investigación II"], requiere: ["Gestión e Investigación en Salud IV"] },
      { nombre: "Anatomía Radiológica II", abre: ["Patología Radiológica"], requiere: ["Anatomía Radiológica I"] },
      { nombre: "Técnicas Radiológicas II", abre: ["Técnicas Radiológicas III", "Práctica Hospitalaria"], requiere: ["Técnicas Radiológicas I"] },
      { nombre: "Dosimetría y Protección Radiológica", requiere: ["Física Aplicada II"] }
    ]
  },
  {
    semestre: "Semestre VII",
    ramos: [
      { nombre: "Sistema Endocrino y Reproductor", abre: ["Módulo Integrado Enfermedades Prioritarias y Aspectos Legales"] },
      { nombre: "Investigación II", abre: ["Seminario Gestión o Investigación I"], requiere: ["Investigación I"] },
      { nombre: "Patología Radiológica", abre: ["Tomografía Axial Computada"], requiere: ["Anatomía Radiológica II"] },
      { nombre: "Técnicas Radiológicas III", abre: ["Tomografía Axial Computada", "Resonancia Nuclear Magnética"], requiere: ["Técnicas Radiológicas II"] },
      { nombre: "Práctica Hospitalaria", requiere: ["Técnicas Radiológicas II"] },
      { nombre: "Electivo" }
    ]
  },
  {
    semestre: "Semestre VIII",
    ramos: [
      { nombre: "Sistema Inmune", abre: ["Módulo Integrado Enfermedades Prioritarias y Aspectos Legales"] },
      { nombre: "Seminario Gestión o Investigación I", requiere: ["Investigación II"] },
      { nombre: "Tomografía Axial Computada", abre: ["Radioterapia"], requiere: ["Técnicas Radiológicas III", "Patología Radiológica"] },
      { nombre: "Resonancia Nuclear Magnética", abre: ["Radioterapia", "Medicina Nuclear"], requiere: ["Técnicas Radiológicas III"] }
    ]
  }
];

const mallaDiv = document.getElementById("malla");
const cursoMap = {};

cursos.forEach(bloque => {
  const label = document.createElement("div");
  label.textContent = bloque.semestre;
  label.className = "semestre-label";
  mallaDiv.appendChild(label);

  bloque.ramos.forEach(curso => {
    const div = document.createElement("div");
    div.className = "curso";
    div.textContent = curso.nombre;
    curso.elemento = div;
    cursoMap[curso.nombre] = curso;
    mallaDiv.appendChild(div);
  });
});

function actualizarEstado() {
  cursos.flatMap(b => b.ramos).forEach(curso => {
    const requisitos = curso.requiere || [];
    const desbloqueado = requisitos.every(req => cursoMap[req]?.aprobado);
    curso.elemento.classList.toggle("desbloqueado", desbloqueado || requisitos.length === 0);
  });
}

cursos.flatMap(b => b.ramos).forEach(curso => {
  curso.elemento.addEventListener("click", () => {
    if (!curso.elemento.classList.contains("desbloqueado")) return;
    curso.aprobado = !curso.aprobado;
    curso.elemento.classList.toggle("aprobado", curso.aprobado);
    actualizarEstado();
  });
});

actualizarEstado();
