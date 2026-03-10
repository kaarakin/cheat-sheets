# Git Cheat Sheet

Связать локальный репозиторий с удаленным:

    git remote add origin url

Просмотр удаленных репозиториев:
    
    git remote -v

Просмотр веток удаленного репозитория:

    git branch -r

Отправить изменения в ветку `branch-name` удаленного репозитория `origin`:

    git push origin branch-name

Получить изменения ветки `branch-name` удаленного репозитория `origin`:

    git pull origin branch-name

Получить изменения из удаленного репозитория `origin` не применяя:

    git fetch origin

Сравнить локальную ветку с веткой `branch-name` из удаленного репозитория `origin`:

    git diff HEAD origin/branch-name

Убрать файл `file-name` из индекса:

    git reset HEAD file-name

Отменить изменения файла `file-name`:

    git checkout file-name

Откатиться к последнему коммиту:

    git reset --hard HEAD

Выполинть слияние с веткой `branch-name` без быстрой перемотки (no fast-forward). В данном случае в истории изменений будет обязательно показано объединение веток:

    git merge --no-ff branch-name

Удалить ветку `old-branch-name` после слияния:

    git branch -d old-branch-name

Удалить ветку `branch-name` в удаленном репозитории `origin`:

    git push origin --delete branch-name
