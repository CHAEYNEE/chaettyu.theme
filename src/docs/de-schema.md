# 📦 DB 설계 문서 – 채뜌.theme

## 👤 profiles (사용자 추가 정보)

| 필드명     | 타입      | 설명                             |
| ---------- | --------- | -------------------------------- |
| id         | UUID      | Supabase auth.users.id와 동일    |
| email      | text      | 이메일 주소                      |
| nickname   | text      | 유저 닉네임                      |
| avatar_url | text      | 프로필 이미지 URL (선택)         |
| created_at | timestamp | 가입 시간                        |
| is_admin   | boolean   | 관리자 여부 (업로드 권한 관리용) |

---

## 🎨 themes (테마 정보)

| 필드명      | 타입      | 설명                             |
| ----------- | --------- | -------------------------------- |
| id          | UUID      | 테마 고유 ID                     |
| user_id     | UUID      | 업로드한 사용자 ID (profiles.id) |
| title       | text      | 테마 이름                        |
| description | text      | 테마 설명                        |
| tags        | text[]    | 테마 태그                        |
| category    | text      | 카테고리 (ex. 파스텔, 키치 등)   |
| image_url   | text      | 대표 이미지 URL                  |
| zip_url     | text      | 테마 zip 파일 주소               |
| price       | numeric   | 가격 (0이면 무료)                |
| is_paid     | boolean   | 유료 여부                        |
| downloads   | integer   | 다운로드 수                      |
| created_at  | timestamp | 등록일                           |

---

## 🖼 theme_images (선택: 상세 이미지 다수)

| 필드명    | 타입 | 설명            |
| --------- | ---- | --------------- |
| id        | UUID | 고유 ID         |
| theme_id  | UUID | 연결된 theme ID |
| image_url | text | 이미지 주소     |
| order     | int  | 정렬 순서       |

---

## 💳 payments (예정: 결제 이력)

| 필드명   | 타입      | 설명                       |
| -------- | --------- | -------------------------- |
| id       | UUID      | 고유 결제 ID               |
| user_id  | UUID      | 결제한 유저 ID             |
| theme_id | UUID      | 구매한 테마 ID             |
| amount   | numeric   | 결제 금액                  |
| paid_at  | timestamp | 결제 일자                  |
| method   | text      | 결제 수단 (toss, kakao 등) |

---
