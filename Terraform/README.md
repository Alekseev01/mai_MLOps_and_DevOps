# MLOps Project: Terraform-проект для создания S3-бакета и ВМ в Yandex Cloud

## 📘 Описание проекта

Проект представляет собой пример инфраструктуры как кода (IaC) на базе Terraform, предназначенной для развёртывания ресурсов в Yandex Cloud. В процессе автоматически создаются:

- **S3-бакет** — облачное хранилище для файлов;
- **Виртуальная машина (VM)** — настраивается через `cloud-init`, получает доступ к S3 с использованием AWS CLI;
- **Сетевая инфраструктура** — VPC и подсеть для размещения ВМ.

Совокупно демонстрируются принципы **модульности**, **переиспользуемости**, а также **безопасной и управляемой автоматизации облачных ресурсов**.

---

## 🧩 Что такое Terraform и зачем он нужен

[Terraform]— это инструмент для управления инфраструктурой с помощью кода (Infrastructure as Code, **IaC**), разработанный компанией HashiCorp.

### Преимущества Terraform:

- ✅ **Декларативный подход**: описывается *что должно быть*, а не *как это создать*.
- ♻️ **Идемпотентность**: повторный запуск `apply` не приведёт к повторному созданию ресурсов.
- 🧩 **Поддержка модулей**: легко повторно использовать конфигурации и делить проект на логические части.
- ☁️ **Мультиоблачность**: работает не только с Yandex Cloud, но и с AWS, GCP, Azure и др.
- 🔒 **Контроль версий**: конфигурации хранятся в Git и могут отслеживаться как обычный код.
- 🚀 **Автоматизация CI/CD**: Terraform можно использовать в DevOps пайплайнах, интегрируя его с GitHub Actions, GitLab CI и др.

Terraform — это современный стандарт в управлении инфраструктурой, позволяющий сделать её предсказуемой, воспроизводимой и удобной для командной работы.

---

## 🗂️ Структура проекта

```
.
├── .gitignire
├── cloud-init.yaml
├── main.tf
├── provider.tf
├── sa-key.json
├── terraform.tfvars
├── variables.tf
└── modules/
    └── s3/
        ├── main.tf
        ├── outputs.tf
        ├── variables.tf
        └── versions.tf
```

## ⚙️ Как это работает

1. **Инициализация Terraform**:  
   `terraform init`

2. **Планирование изменений**:  
   `terraform plan -out=nametest`

3. **Применение изменений**:  
   `terraform apply "nametest"`

4. **VM настраивается автоматически**:  
   Скрипт `cloud-init.yaml` устанавливает AWS CLI, прописывает ключи и загружает файл в S3.

В результате:
- Создаются ресурсы в Yandex Cloud.
- ВМ автоматически настраивается и получает доступ к S3-бакету.
- Всё управляется и отслеживается через Terraform.

---

## 🎯 Полезность проекта

- **Автоматизация**: нет необходимости вручную настраивать инфраструктуру.
- **Масштабируемость**: подход легко адаптируется под несколько бакетов или машин.
- **Повторяемость**: проект можно легко развернуть в любой момент с теми же параметрами.
- **Разделение на модули**: упрощает повторное использование кода и поддержку.
- **Практика IaC (Infrastructure as Code)**: улучшает управляемость и версионирование инфраструктуры.

---

## ✅ Требования

- Terraform
- Аккаунт в Yandex Cloud
- Сервисный аккаунт с ролями

---

## 📝 Заключение

Проект выполнен в рамках практического задания.  
Все настройки протестированы в среде Yandex Cloud.

Возможные сценарии использования:

- Создание учебных и тестовых окружений.
- Хранение данных с доступом из облачных ВМ.
- Быстрое прототипирование проектов.
- Демонстрация DevOps-автоматизации в дальнейшей работе.

Таким образом, проект получился несложный, но послужил наглядным примером эффективности использования Terraform для развёртывания инфраструктуры в Yandex Cloud. Подчеркнул ценность подхода Infrastructure as Code, а так же возможности к масштабируемым и надёжным облачным решениям.