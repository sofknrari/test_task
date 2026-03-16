## Тестовое задание для Уно-Софт
В рамках задачи реализовал установку и конфигурирование ldap сервера на ubuntu.
Ссылка на полученное задание: https://github.com/PeacockTeam/new-job/blob/master/DevOps-Ansible.md



## Инструкция по запуску

### 1. Подготовка пароля Vault
Если переменная окружения еще не настроена в вашей сессии, выполните экспорт (путь к файлу с паролем):

```bash
export ANSIBLE_VAULT_PASSWORD_FILE=.vp
```

### 2. Установка зависимостей
Для работы с LDAP необходима коллекция `community.general`:

```bash
ansible-galaxy collection install -r requirements.yml
```

### 3. Настройка переменных
Отредактируйте `inventory.ini`, указав IP вашего сервера.
Отредактируйте `secrets.yml` 

### 4. Зашифровка переменных
Зашифруйте файл `secrets.yml`:

```bash
ansible-vault encrypt secrets.yml
```

### 5. Запуск плейбука
Запуск выполняется от имени пользователя `root` (или с использованием `--become`):

```bash
ansible-playbook playbook.yml -u root
```

## Проверка результата
После успешного запуска можно проверить записи на сервере:

```bash
ldapsearch -x -b "dc=example,dc=com" -H ldap://localhost
```
