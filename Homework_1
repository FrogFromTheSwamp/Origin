class Student:
    def __init__(self, name, surname, gender):
        self.name = name
        self.surname = surname
        self.gender = gender
        self.finished_courses = []
        self.courses_in_progress = []
        self.grades = {}
        self.average_rating = float()

    def rate_lc(self, lect, course, grade):
        if isinstance(lect, Lecturer) and course in lect.courses_attached and course in self.courses_in_progress:
            if course in lect.grades_dict:
                lect.grades_dict += {course: grade}
            else:
                lect.grades_dict = {course: grade}
        else:
            return 'Ошибка'

    def average_hw(self, kol = 0):
        for value in self.grades.values():
            kol += len(value)
        self.average_rating = round(sum(map(sum, self.grades.values())) / kol, 1)
        return self.average_rating

    def __str__(self):
        print(f"Имя: {self.name}")
        print(f"Фамилия: {self.surname}")
        print(f"Средняя оценка: {self.average_hw()}")
        print(f'Курсы в процессе изучения: {", ".join(self.courses_in_progress)}')
        print(f'Завершенные курсы: {", ".join(self.finished_courses)}')
        return ("")

    def __lt__(self, other):
      if not isinstance(other, Student):
          print('Это не студент!')
          return
      return self.average_rating < other.average_rating

class Mentor:
    def __init__(self, name, surname):
        self.name = name
        self.surname = surname
        self.courses_attached = []

class Lecturer(Mentor):
    def __init__(self, name, surname):
      super().__init__(name, surname)
      self.average_rating = float()
      self.grades_dict = {}

    def average_rat(self, kol=0):
        for value in self.grades_dict.values():
            kol += len(value)
        self.average_rating = round(sum(map(sum, self.grades_dict.values())) / kol, 1)
        return self.average_rating 

    def __str__(self):
        print(f"Имя: {self.name}")
        print(f"Фамилия: {self.surname}")
        print(f"Средняя оценка за лекции: {self.average_rat()}")
        return " "

    def __lt__(self, other):
        if not isinstance(other, Lecturer):
            print('Это не лектор!')
            return 
        return self.average_rating < other.average_rating


class Reviewer(Mentor):
    def __str__(self):
        print(f"Имя: {self.name}")
        print(f"Фамилия: {self.surname}")
        return " "
      
    def rate_hw(self, student, course, grade):
        if isinstance(student, Student) and course in self.courses_attached and course in student.courses_in_progress:
            if course in student.grades:
                student.grades[course] += [grade]
            else:
                student.grades[course] = [grade]
        else:
            return 'Ошибка'

student1 = Student('Семён', 'Петров', 'Мужской')
student2 = Student('Анна', 'Кудряшова', 'Женский')
best_student = Student('Ruoy', 'Eman', 'your_gender')
mentor1 = Mentor('Сергей', 'Иванов')
mentor2 = Mentor('Виктория', 'Шилова')
lecturer1 = Lecturer('Андрей', 'Жуковский')
lecturer2 = Lecturer('Владислава', 'Шпиляева')
reviewer1 = Reviewer('Вадим', 'Одиноков')
reviewer2 = Reviewer('Денис', 'Лепик')

student1.finished_courses += ['Web']
student2.finished_courses += ['HTML']
best_student.finished_courses += ['HTML']
best_student.finished_courses += ['Web-design']

student1.courses_in_progress += ['Python']
student2.courses_in_progress += ['Python']
best_student.courses_in_progress += ['Python']
best_student.courses_in_progress += ['Java']
student1.courses_in_progress += ['Java']

reviewer1.courses_attached += ['Python']
reviewer1.courses_attached += ['Java']
reviewer2.courses_attached += ['Python']
reviewer2.courses_attached += ['Java']
lecturer1.courses_attached += ['Python']
lecturer2.courses_attached += ['Python']

reviewer1.rate_hw(student1, 'Python', 5)
reviewer1.rate_hw(student1, 'Java', 8)
reviewer1.rate_hw(best_student, 'Java', 6)
reviewer1.rate_hw(best_student, 'Java', 3)
reviewer2.rate_hw(student2, 'Python', 9)

student1.rate_lc(lecturer1, 'Python', [8])
student2.rate_lc(lecturer2, 'Python', [10])

print(student1)
print(student2)
print(best_student)

print(lecturer1)
print(lecturer2)

print(reviewer1)
print(reviewer2)

print(lecturer1.__lt__(lecturer2))
print(student1.__lt__(student2))

#функции
students_list = [best_student, student1, student2]
def average_homework(student_list, course):
    kol = 0
    aver = 0
    for student in student_list:
      if  [course] == student.courses_in_progress:
          kol += 1
          aver += student.average_rating
    average = aver / kol
    return average        

lecturers_list = [lecturer1, lecturer2]
def average_lc(lecturer_list, course_name):
  count = 0
  sum = 0
  for lecturer in lecturers_list:
    if [course_name] == lecturer.courses_attached:
      count +=1
      sum += lecturer.average_rating
  average_lec = round(sum / count, 1)
  return average_lec

print(f"Средняя оценка за домашнее задание у всех студентов по курсу Python: {average_homework(students_list, 'Python')}")

print(f"Средняя оценка за лекции всех лекторов по курсу Python: {average_lc(lecturers_list, 'Python')}")