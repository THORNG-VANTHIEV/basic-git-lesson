# 📘 មេរៀន: Git Command Line Basics

Git គឺជាប្រព័ន្ធ **version control system** ដែលជួយតាមដានការផ្លាស់ប្តូរនៅក្នុង project របស់អ្នក, ធ្វើការរួមគ្នាជាមួយអ្នកផ្សេងទៀត, ហើយត្រឡប់ទៅកំណែចាស់បាន។

---

## 🔹 1. Check Git Version
```bash
git --version
```
👉 ពិនិត្យមើលថា Git ត្រូវបានដំឡើងរួចហើយ និងបង្ហាញកំណែ។

---

## 🔹 2. Configure Git (first time setup)
```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```
👉 កំណត់ឈ្មោះ និងអ៊ីមែលសម្រាប់ commit (ដើម្បីឲ្យ Git ដឹងថានរណាធ្វើការផ្លាស់ប្តូរ)។

ពិនិត្យ config:
```bash
git config --list
```

---

## 🔹 3. Initialize a Repository
```bash
git init
```
👉 បង្កើត Git repository ថ្មីនៅក្នុង folder បច្ចុប្បន្ន។  
(វានឹងបង្កើត `.git` folder សម្ងាត់សម្រាប់រក្សាទុកប្រវត្តិ និង config។)

---

## 🔹 4. Clone a Repository
```bash
git clone https://github.com/user/repo.git
```
👉 ទាញយក project ពី GitHub (ឬ Git server ផ្សេងទៀត) មកកុំព្យូទ័រ។

---

## 🔹 5. Check Status
```bash
git status
```
👉 បង្ហាញស្ថានភាព project (file ថ្មី, បានកែប្រែ ឬ staged)។

---

## 🔹 6. Add Files
```bash
git add file.txt
```
👉 ដាក់ file មួយទៅក្នុង stage ដើម្បី commit។  

ដាក់ទាំងអស់:
```bash
git add .
```

---

## 🔹 7. Commit Changes
```bash
git commit -m "Add new feature"
```
👉 រក្សាទុកការផ្លាស់ប្តូរដែលបាន staged ជាមួយសារមួយ។

---

## 🔹 8. See History
```bash
git log
```
👉 បង្ហាញប្រវត្តិ commit (នរណា, ពេលណា, និងអ្វី)។  

កំណែខ្លី:
```bash
git log --oneline
```

---

## 🔹 9. Create & Switch Branches
បង្កើត branch:
```bash
git branch feature-login
```

ប្តូរទៅ branch:
```bash
git checkout feature-login
```

Shortcut (បង្កើត + ប្តូរ):
```bash
git checkout -b feature-login
```

👉 Branches អនុញ្ញាតឲ្យអ្នកធ្វើការលើ feature ថ្មីដោយមិនបំផ្លាញ `main`។

---

## 🔹 10. Merge Branches
ប្តូរទៅ main branch:
```bash
git checkout main
```

បញ្ចូល branch:
```bash
git merge feature-login
```

👉 រួមបញ្ចូលការផ្លាស់ប្តូរ ពី `feature-login` ទៅក្នុង `main`។

---

## 🔹 11. Remote Repositories
បន្ថែម remote:
```bash
git remote add origin https://github.com/user/repo.git
```

ពិនិត្យ remotes:
```bash
git remote -v
```

---

## 🔹 12. Push Changes
```bash
git push -u origin main
```
👉 ផ្ញើ commit ទៅ GitHub (`-u` កំណត់ default upstream)។

---

## 🔹 13. Pull Updates
```bash
git pull origin main
```
👉 ទាញយកនិងរួមបញ្ចូល update ពី GitHub មក local branch។

---

## 🔹 14. Discard Changes
បោះបង់ការផ្លាស់ប្តូរ file:
```bash
git checkout -- file.txt
```

ដកចេញពី staged:
```bash
git reset file.txt
```

---

## 🔹 15. Useful Shortcuts
- មើលភាពខុសគ្នានៅក្នុង code:
```bash
git diff
```

- លុប branch:
```bash
git branch -d feature-login
```

---

# 🎯 Example Workflow
1. ចាប់ផ្តើម project ថ្មី:
```bash
mkdir my_project && cd my_project
git init
```

2. បង្កើត file:
```bash
echo "Hello Git" > hello.txt
git add hello.txt
git commit -m "Add hello.txt"
```

3. Push ទៅ GitHub:
```bash
git remote add origin https://github.com/yourname/my_project.git
git branch -M main
git push -u origin main
```

---

👉 នេះគឺជា **មូលដ្ឋាន**។ បើអ្នកអាចយល់ដឹង និងប្រើបានទាំងនេះ អ្នកអាចដោះស្រាយការងារ Git ប្រចាំថ្ងៃ 90% បានហើយ។
