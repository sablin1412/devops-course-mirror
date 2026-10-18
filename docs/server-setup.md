# Конфигурация виртуальной машины devops-vm

## 1. Параметры машины
- Объём оперативной памяти: 2048 МБ
- Количество ядер процессора: 2
- Объём дискового накопителя: 25 ГБ (динамический)

## 2. Сетевые интерфейсы
- Адаптер 1: NAT (10.0.2.15) — доступ гостевой ОС в интернет.
- Адаптер 2: Host-only (192.168.56.101) — прямой доступ с хостовой ОС.

## 3. Правило проброса портов
- Порт хостовой системы: 2222
- Порт гостевой системы: 22

## 4. Учётные записи
- `student` (группы: sudo), парольная аутентификация.
- `devops` (группы: sudo), ключевая аутентификация (ed25519).

## 5. Служба SSH
- Порт: 2222
- Изменённые директивы: PermitRootLogin no, PasswordAuthentication no, PubkeyAuthentication yes, PermitEmptyPasswords no, MaxAuthTries 3, LoginGraceTime 30, AllowUsers devops, X11Forwarding no, ClientAliveInterval 300, ClientAliveCountMax 2.
- Файл конфигурации: `/etc/ssh/sshd_config.d/99-hardening.conf`

## 6. Правила межсетевого экрана
- Политики по умолчанию: deny incoming, allow outgoing.
- Правила: 80/tcp ALLOW, 443/tcp ALLOW, 2222/tcp LIMIT.

## 7. Снимки состояния
- 01-clean-install
- 02-keys-configured
- 03-ssh-hardened
