type Student = {
  id: number;
  name: string;
  age: number;
  grades: number[];
  hobby?: string;
};

const students: Student[] = [
  { id: 1, name: "Ihsan", age: 17, grades: [5, 4, 5], hobby: "sport" },
  { id: 2, name: "David", age: 17, grades: [4, 3, 4] },
  { id: 3, name: "Imran", age: 18, grades: [5, 5, 5, 5], hobby: "music" },
  { id: 4, name: "Amir", age: 18, grades: [3, 4] },
  { id: 5, name: "Samira", age: 19, grades: [4, 4, 5], hobby: "chess" },
];

function addStudent(student: Student): void {
  const exists = students.some(s => s.id === student.id);

  if (exists) {
    console.log("Студент с таким id уже существует");
    return;
  }

  students.push(student);
}

function findTopStudent(list: Student[]): Student {
  let topStudent = list[0];

  for (const student of list) {
    if (student.grades.length > topStudent.grades.length) {
      topStudent = student;
    }
  }

  return topStudent;
}

function updateStudentHobby(id: number, hobby: string): void {
  const student = students.find(s => s.id === id);

  if (!student) {
    console.log("Не найден");
    return;
  }

  student.hobby = hobby;
}

addStudent({
  id: 6,
  name: "Ihsan",
  age: 17,
  grades: [5, 4, 5],
  hobby: "sport"
});

addStudent({
  id: 1,
  name: "Imran",
  age: 18,
  grades: [5, 5, 5, 5]
  hobby: "music",
});

updateStudentHobby(3, "reading");
updateStudentHobby(99, "none");

const bestStudent = findTopStudent(students);
console.log("Луйчший студент:", bestStudent);
console.log("Все студенты:", students);

