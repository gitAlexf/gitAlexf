

# Git Cheatsheet — VoltCycle Operations (BAS)

Коротка шпаргалка з трьома основними сценаріями роботи з git для проекту в SAP Business Application Studio.

---

## 1. Запушити проект з BAS у GitHub (вперше)

```bash
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/<логін>/<репо>.git
git branch -M main
git push -u origin main
```

> Перед `git add .` перевірте, що є `.gitignore` (виключає `node_modules/`, `.env`, `gen/`, `db/*.db`).

---

## 2. Розгорнути проект на іншому BAS

```bash
git clone https://github.com/<логін>/<репо>.git
cd <репо>
npm install
cds watch
```

> Файли `.env` / секрети не зберігаються в git — їх треба створити вручну на новому середовищі.

---

## 3. Зберегти копію поточного стану у свій репозиторій

Коли основний `origin` — це спільний репозиторій (наприклад, для перевірки викладачем), а хочете зберегти бекап у своєму особистому репо:

```bash
git remote add backup https://github.com/<логін>/<репо>.git
git push backup HEAD:main
```

> `git remote -v` — перевірити, які remote вже підключені.
> Наступного разу просто повторюйте `git push backup HEAD:main`, remote додавати вже не треба.

---

## Корисні команди

```bash
git status          # що змінилось
git remote -v        # список підключених remote
git log --oneline -5 # останні коміти
```
