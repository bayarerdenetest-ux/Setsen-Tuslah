### 1. Анхны тохиргоо

Нэг удаа өөрийн нэр, имэйлийг тохируулна.

git config --global user.name "Таны нэр"
git config --global user.email "you@example.com"

### 2. GitHub-аас төсөл татах

git clone https://github.com/USERNAME/REPOSITORY.git
cd REPOSITORY

- clone — төслийг өөрийн компьютерт хуулж татна.
- cd — төслийн хавтас руу орно.
- USERNAME, REPOSITORY хэсгийг бодит нэрээр солино.

### 3. Өөрчлөлтөө хадгалж, GitHub руу оруулах

git status
git diff
git add .
git commit -m "Нэвтрэх хуудас нэмэв"
git push

| Команд | Тайлбар |
|---|---|
| git status | Ямар файл өөрчлөгдсөнийг харуулна. |
| git diff | Файлын аль мөрүүд өөрчлөгдсөнийг харуулна. |
| git add . | Одоогийн хавтас болон доторх өөрчлөлтүүдийг дараагийн commit-д бэлтгэнэ. |
| git commit -m "Тайлбар" | Бэлтгэсэн өөрчлөлтийг тайлбартайгаар компьютерт хадгална. |
| git push | Хадгалсан commit-уудыг GitHub руу илгээнэ. |

Зөвхөн нэг файлыг бэлтгэх бол:

git add main.py

### 4. GitHub дахь шинэ өөрчлөлтийг авах

git pull

Холбогдсон салбарын шинэ commit-уудыг татаж, өөрийн салбарт нэгтгэнэ.

### 5. Салбар буюу branch ашиглах

Branch нь шинэ боломж, засвар дээр тусдаа ажиллахад хэрэглэгдэнэ.

git branch                       # Өөрийн компьютер дахь салбаруудыг харах
git switch -c feature-login       # Шинэ салбар үүсгээд түүн рүү шилжих
git switch main                   # main салбар руу шилжих
git switch feature-login          # feature-login салбар руу буцах
git push -u origin feature-login  # Салбарыг GitHub руу анх удаа илгээх

Дараа нь GitHub дээр Pull request нээж, өөрчлөлтөө main салбарт нэгтгэх санал гаргана.

### 6. Өөрийн төслийг анх GitHub руу оруулах

GitHub дээр README, .gitignore, license нэмэлгүй хоосон repository үүсгээд, төслийн хавтас дотроос ажиллуулна:

git init
git add .
git commit -m "Төслийн эхний хувилбар"
git branch -M main
git remote add origin https://github.com/USERNAME/REPOSITORY.git
git push -u origin main

| Команд | Тайлбар |
|---|---|
| git init | Тухайн хавтсанд Git ашиглаж эхэлнэ. |
| git branch -M main | Одоогийн салбарыг main гэж нэрлэнэ. |
| git remote add origin URL | GitHub repository-ийн хаягийг origin нэрээр холбоно. |
| git push -u origin main | main салбарыг илгээж, цаашдын push, pull холбоосыг тохируулна. |

### 7. Түүх харах, өөрчлөлт буцаах

git log --oneline

Commit-уудын товч түүх болон ID-г харуулна.

git restore --staged main.py

Файлыг commit-д бэлтгэсэн төлөвөөс гаргана. Бичсэн өөрчлөлт хэвээр үлдэнэ.

git restore main.py

⚠️ Файлын stage хийгээгүй өөрчлөлтийг устгана. Анхааралтай хэрэглээрэй.

git revert COMMIT_ID

Өмнөх commit-ийн өөрчлөлтийг эсрэгээр нь буцаасан шинэ commit үүсгэнэ.

### 8. Дуусаагүй ажлаа түр хадгалах

git stash       # Өөрчлөлтөө түр хадгалаад ажлын хавтсыг цэвэрлэх
git stash pop   # Түр хадгалсан өөрчлөлтөө буцааж гаргах

Шинээр үүсгэсэн, Git-д бүртгэгдээгүй файлуудыг хамт хадгалах бол git stash -u хэрэглэнэ.

### 9. Git-д оруулахгүй файлууд — .gitignore

Төслийн үндсэн хавтсанд .gitignore файл үүсгэнэ:

.env
node_modules/
__pycache__/
*.log

Энэ нь нууц тохиргоо, суулгасан сан, түр файлуудыг Git-д шинээр бүртгэхээс сэргийлнэ. Аль хэдийн бүртгэгдсэн файлд автоматаар үйлчлэхгүй.

Өдөр тутмын дараалал:

git pull → кодоо засах → git add . → git commit -m "Тайлбар" → git push