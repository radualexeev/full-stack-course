# 📝 Домашнее задание — Lesson 1 (Git Basics)

## 🔀 Работа с веткой
Перед выполнением заданий работай **в отдельной ветке**, чтобы не трогать `main`.

Создай ветку:
```bash
git checkout -b homework/lesson1
```

Проверь текущую ветку:
```bash
git branch
```
(рядом с `homework/lesson1` будет `*`)

Отправляй изменения так:
```bash
git push origin homework/lesson1
```

---

## 📘 Задания

### ✅ Задание 1 — Создание файла
1. Создай файл `task1.txt` в папке `lesson1/homework/`.  
2. Напиши в нём:  
   ```
   Это моё первое домашнее задание по Git.
   ```
3. Сделай коммит:
   ```bash
   git add lesson1/homework/task1.txt
   git commit -m "docs: добавлен task1.txt"
   git push origin homework/lesson1
   ```

---

### ✏️ Задание 2 — Изменение файла
1. Добавь во `task1.txt` строку:  
   ```
   Я учусь работать с Git.
   ```
2. Сделай коммит:
   ```bash
   git add lesson1/homework/task1.txt
   git commit -m "docs: обновлён task1.txt"
   git push origin homework/lesson1
   ```

---

### 📄 Задание 3 — Новый файл
1. Создай файл `task2.txt`.  
2. Напиши список из 3 слов (например: кот, собака, птица).  
3. Сделай коммит:
   ```bash
   git add lesson1/homework/task2.txt
   git commit -m "docs: добавлен task2.txt"
   git push origin homework/lesson1
   ```

---

### 🗑 Задание 4 — Удаление файла
1. Удали `task2.txt`.  
2. Зафиксируй удаление:
   ```bash
   git rm lesson1/homework/task2.txt
   git commit -m "chore: удалён task2.txt"
   git push origin homework/lesson1
   ```

---

### 📌 Задание 5 — Итоговый файл
1. Создай файл `summary.txt`.  
2. Напиши:
   ```
   Сегодня я научился:
   - создавать файлы
   - изменять файлы
   - удалять файлы
   - делать коммиты
   - пушить на GitHub
   ```
3. Сделай коммит:
   ```bash
   git add lesson1/homework/summary.txt
   git commit -m "docs: добавлен summary.txt"
   git push origin homework/lesson1
   ```

---

## 🎯 Результат
После выполнения всех заданий в папке `lesson1/homework/` должны остаться:
- `task1.txt`
- `summary.txt`
