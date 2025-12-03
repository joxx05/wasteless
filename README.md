# Wasteless — Nền tảng Golang với kiến trúc giống Django

Wasteless là một nền tảng backend được xây dựng bằng **Golang**, lấy cảm hứng từ cấu trúc của **Django** để mang lại tính trực quan, dễ mở rộng và dễ tổ chức mã nguồn. Mục tiêu của dự án là cung cấp một kiến trúc rõ ràng, tách biệt giữa các tầng, phù hợp cho các hệ thống lớn, có thể mở rộng (scalable).

---

## 🚀 Mục tiêu kiến trúc

* Giữ được sự **mạch lạc và quen thuộc** như Django.
* Tách rõ ràng: **config**, **apps**, **models**, **views**, **services**, **templates**, **static**, **migrations**.
* Mỗi tính năng (feature) nằm trong 1 **app** riêng — dễ mở rộng, dễ bảo trì.
* Hỗ trợ REST API với **Gin**, hoặc GraphQL tùy nhu cầu.

---

## 📁 Cấu trúc dự án

```
wasteless/
│── manage.go              # tương đương manage.py
│
│── config/                # giống Django project/settings.py
│   ├── settings.go
│   ├── router.go          # giống urls.py
│   └── middleware.go
│
│── apps/                  # y chang Django "apps"
│   ├── user/
│   │   ├── models.go      # models.py
│   │   ├── views.go       # views.py
│   │   ├── urls.go        # urls.py
│   │   ├── forms.go       # forms.py
│   │   └── services.go    # business logic
│   │
│   └── product/
│       ├── models.go
│       ├── views.go
│       ├── urls.go
│       ├── forms.go
│       └── services.go
│
│── templates/             # y chang Django templates/
│   ├── base.html
│   └── user/
│        └── list.html
│
│── static/                # giống Django static/
│   ├── css/
│   ├── js/
│   └── images/
│
│── migrations/            # tương đương Django migrations
│   └── *.sql
│
│── go.mod
```

---

## 🔧 Thành phần chính

### **manage.go** (giống manage.py)

* Chạy server
* Tạo migrations
* Chạy lệnh CLI nội bộ

### **config/**

* `settings.go`: cấu hình database, JWT, các biến môi trường...
* `router.go`: đăng ký routes từ từng app
* `middleware.go`: middleware (auth, logging, rate limit...)

### **apps/**

Mỗi app có đầy đủ:

* `models.go` — ORM hoặc struct đại diện entity
* `views.go` — handler trả về response
* `urls.go` — định nghĩa route cho app
* `services.go` — business logic
* `forms.go` — validate dữ liệu đầu vào (giống Django forms)

### **templates/** & **static/**

* Hỗ trợ render HTML nếu dùng server-side rendering

### **migrations/**

* Lưu trữ file SQL để migrate thủ công hoặc tự động

---

## 🧩 Lợi ích của kiến trúc này

* **Dễ học** nếu bạn quen Django
* **Clean architecture** — tách biệt logic rõ ràng
* **Không rối** như việc nhét toàn bộ route vào một file
* **Dễ mở rộng**: thêm app mới = thêm thư mục trong `apps/`
* **Dùng được cho REST API, GraphQL hoặc template render**

---

## ▶️ Chạy dự án

```
go run manage.go runserver
```

---

## 🎯 Kế hoạch phát triển

* [ ] Authentication + JWT
* [ ] Pagination chuẩn Django
* [ ] Admin panel giống Django Admin
* [ ] Task queue (giống Celery nhưng dùng Go)
* [ ] Websocket hỗ trợ real-time

---

## ❤️ Mục tiêu cuối cùng

Tạo ra một **framework mini giống Django nhưng viết bằng Golang**, mạnh, sạch sẽ và dễ mở rộng cho các dự án lớn.

---

Nếu muốn thêm badge, logo, hoặc hướng dẫn cài đặt chi tiết, cứ nói mình thêm nhé!
