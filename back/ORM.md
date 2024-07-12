# Node에서 주로 사용되는 ORM에 대해 알아보고자 한다.

아래 그림은 ossinsight.io에서 Javascript ORM의 Stars 수에 대하여 순위를 매긴 이미지이다.
![javascript ORM - Stars](https://github.com/user-attachments/assets/0d69ef3a-e605-401c-b913-72ce4c6e2ece)

stars 수 뿐만 아니라 Pull Requests, Pull Request Creators, Issues 으로 항목을 나누어 순위를 매겼으며 자세한 순위가 궁금하면 [ossinsight.io](https://ossinsight.io/collections/javascript-orm/?monthly-rankings=prs&historical-rankings=prs)
에서 직접 확인해보는 것도 좋다. 
Javascript ORM 순위를 보면 많은 사람들이 prisma, typeorm, sequelize, mongoose, drizzle-orm, mikro-orm 등에 관심을 가지며, 또한 많이 사용하고 있다는 것을 알 수 있다.

그렇다면, 각 ORM에 대해 알아보고 현재 프로젝트에 적용하기 적합한 js ORM 을 알아보고자 한다.

## Prisma
- 선언적인 모델을 정의해서 복잡한 모델 인스턴스를 관리하는데 안전하게 데이터를 읽고 쓸 수 있음
- 타입스크립트와 함께 사용하기 최적화된 ORM으로 타입 안정성 보장
- 자동 생성되는 스키마와 마이그레이션 도구

## TypeORM
- 타입스크립트와 자바스크립트에서 사용 가능한 ORM
- sequelize 과 prisma 보다 좋은 성능 [sequelize 성능 비교](https://kyungyeon.dev/posts/3), [prisma 성능 비교](https://wwlee94.github.io/category/blog/performance-comparison-prisma-typeorm/)
- Nest.js와 잘 맞으며, 플러그인 확장이나 모델 기반 플러그인 개발이 용이한 편이지만, 런타임 에러 등 메이저 버그도 간간히 발생

## Sequelize
- Promise 기반 비동기 작업 처리
- 타입스크립트 지원이 약해 타입 안정성이 부족하다.

## Mongoose
- MongoDB를 위한 ODM
- 스키마와 모델을 통해 data 를 불러오고 객체화하여 데이터에 접근
- SQL DB를 지원하지 않음

## Drizzle-ORM
- 새로운 경량 ORM으로 주로 타입스크립트와 함께 사용
- 상대적으로 작은 커뮤니티와 기능이 제한적
  
## mikro-orm
- 자바스크립트와 타입스크립트 둘다 지원하며, RDB 뿐만 아니라 NoSQL 도 지원한다.
- 초기 설정 및 학습 곡선이 다소 있음

# 결론
각 ORM의 특징을 통해 사이드 프로젝트로 TypeORM 사용해보는 것이 줄을 것이라 생각한다.
TypeORM은 Nest.js와 통합이 좋고, 학습곡선이 낮으며, 타입스크립트를 사용할 수 있어 타입 안정성을 제공하여 안정적으로 개발 가능할 것이라 생각했다.
물론, 버그와 런타임에서 발생하는 에러 등 완벽하지 못한 모습을 보이긴 하나, 안정성과 성능적인 면에서 우수하다고 판단하였다.
