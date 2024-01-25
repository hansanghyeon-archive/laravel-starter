## Why Laravel?

현재 프론트엔드의 모순

- HTTP만 있을때 Thick client로 발전해왔음
- WebSocket 추가로 Thin client도 가능해짐
- 웹개발의 90% 이상을 차지하는 비즈니스 애플리케이션은 Thin client가 훨씬 생산적임에도 Thick client로 개발되고있다.

https://www.youtube.com/watch?v=lAaD-6OQSHE

Thin client를 손쉽게 만들기위해서 firebase, supabase, pocketbase **realtime** 등장했다 생각한다.
하지만 이건은 DB realtime아닌가? 우리가 원하는 것은 BE, FE의 realtime인데?
phoenix(elixir 기반의 웹프레임워크), livewire(php 기반의 laravel 프레임워크에서 사용가능한 기능)같이 백엔드 realtime이 아닌가?!?! 그래서 이 두가지를 알아봤다.
phoenix를 학습하였지만 phoenix는 너무 학습곡선이 높다.
그래서 일단 laravel의 livewire로 진행한다.

---

## 개인 Laravel 개발 환경

이 저장소에는설치를 기반으로 하는 개인 기본 Laravel 개발 환경 `laravel new`와 `TypeScript` `TailwindCSS`를 설정하기 위한 Laravel Breeze가 포함되어 있습니다. 또한 몇 가지 추가 구성 및 도구가 포함되어 있습니다.

**참고: 이 기본 Laravel 개발 환경은 개인 취향에 따른 것이며 보편적인 설정을 위한 것이 아닙니다.**

## Main Feature

- [Laravel Framework](https://laravel.com/) (version 10.x)
- [Laravel Breeze](https://laravel.com/docs/10.x/starter-kits) (providing [livewire](https://laravel-livewire.com/), [Alpine.js](https://alpinejs.dev/), [TypeScript](https://www.typescriptlang.org/), and [Tailwind CSS](https://tailwindcss.com/))
- [Laravel Sail](https://laravel.com/docs/sail) (lightweight command-line interface for running Laravel in Docker containers, with [MariaDB](https://mariadb.org/) and [Redis](https://redis.io/))
- [Vite](https://vitejs.dev/) (next-generation frontend development and build tool)
- Using [pnpm](https://pnpm.io/) instead of npm (faster and more efficient package manager)

## How to Use

WIP
