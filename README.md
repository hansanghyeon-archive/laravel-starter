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

## 개인 Laravel 개발 환경

이 저장소에는설치를 기반으로 하는 개인 기본 Laravel 개발 환경 `laravel new`와 `TypeScript` `TailwindCSS`를 설정하기 위한 Laravel Breeze가 포함되어 있습니다. 또한 몇 가지 추가 구성 및 도구가 포함되어 있습니다.

**참고: 이 기본 Laravel 개발 환경은 개인 취향에 따른 것이며 보편적인 설정을 위한 것이 아닙니다.**

## Main Feature

- [Laravel Framework](https://laravel.com/) (version 10.x)
- [Laravel Breeze](https://laravel.com/docs/10.x/starter-kits) (providing [livewire](https://laravel-livewire.com/), [Alpine.js](https://alpinejs.dev/), and [Tailwind CSS](https://tailwindcss.com/))
- ⭐️ [Laravel Sail](https://laravel.com/docs/sail) (lightweight command-line interface for running Laravel in Docker containers, with [MariaDB](https://mariadb.org/) and [Redis](https://redis.io/))
- Using [pnpm](https://pnpm.io/) instead of npm (faster and more efficient package manager)
- [Vite](https://vitejs.dev/) (next-generation frontend development and build tool)
- git hook (code linting before commits), [husky](https://github.com/typicode/husky), [nano-stage](https://github.com/usmanyunusov/nano-staged)

## Next Feature

Breeze를 확실하게 익힌후에 Jetstream으로 넘어가는 것을 목표로한다.

- [Laravel Framework](https://laravel.com/) (version 10.x)
- Laravel Jetstream, Tailwind CSS, livewire, Alpine.js, TypeScript
- ⭐️ [Laravel Sail](https://laravel.com/docs/sail) (lightweight command-line interface for running Laravel in Docker containers, with [MariaDB](https://mariadb.org/) and [Redis](https://redis.io/))
- [Vite](https://vitejs.dev/) (next-generation frontend development and build tool)
- Using [pnpm](https://pnpm.io/) instead of npm (faster and more efficient package manager)

필독 - https://jetstream.laravel.com/concept-overview.html

## 셋업 튜토리얼

_PHP, Composer가 설치되어있지 않고 docker, docker composer plugin이 설치되어있는 VM 환경에서 진행됩니다._

### create laravel project

```sh
curl -s https://laravel.build/example-app | bash
```

sail을 재대로 사용하기 위해서 permission을 변경한다.

```sh
chmod -R 775 example-app
```

프로젝트 폴더로 이동

```sh
cd example-app
```

### sail 설정

sail로 라라벨 프로젝트 시작하기 전에 [Laravel Sail - 쉘 별칭 구성](https://laravel.com/docs/10.x/sail#configuring-a-shell-alias) 설정하기

```sh
echo "alias sail='[ -f sail ] && sh sail || sh vendor/bin/sail'" >> ~/.zshrc
source ~/.zshrc
```

> [!IMPORTANT]
> Laravel Sail을 사용할때 애플리케이션은 Docekr 컨테이너 내에서 실행되며 로컬 컴퓨터와 격리됩니다. 그러나 Sail은 임의의 **PHP명령**, **Artisan 명령**, **Composer 명령**, **Node/NPM 명령**에 대한 참조를 자주 볼 수 있습니다.
> 로컬 Laravel 개발 환경에 Sail을 사용하는 경우 Sail을 사용하여 해당 명령을 실행해야 합니다.
> 
> ```sh
> # 로컬에서 artisan 명령어 실행하기
> php artisan queue:work
>
> # Laravel Sail 내에서 artisan 명령어 실행하기
> sail artisan queue:work
> ```

라라벨 프로젝트 시작

```sh
sail up -d
```

### Breeze 설치하기

```sh
sail composer require laravel/breeze --dev
```

```sh
sail artisan breeze:install
```

<img src="https://github.com/Hansanghyeon/laravel-starter/assets/42893446/5bc23897-9368-4108-b180-b56c68b62c64" alt="image" width="518" />

### NODE, pnpm 설정하기

[Node 버전 변경하기](https://laravel.com/docs/9.x/sail#sail-node-versions)

NODE LTS버전은 20이라 20으로 진행.

NODE또한 라라벨 컨테이너에서 작업 (PHP와 동일하게)

```diff
services:
    laravel.test:
        build:
            context: ./vendor/laravel/sail/runtimes/8.3
            dockerfile: Dockerfile
            args:
                WWWGROUP: '${WWWGROUP}'
+               NODE_VERSION: '20'
        image: sail-8.3/app
```

```sh
sail down
sail build --no-cache
sail up -d
```

sail에 npm, yarn, pnpm 모두 설정되어있다.

```sh
sail node -v
sail yarn -v
sail pnpm -v
```

npm 패키지 설치, 실행

```sh
sail pnpm install
sail pnpm run dev
```

<img src="https://github.com/Hansanghyeon/laravel-starter/assets/42893446/670c3288-0f27-4c9d-a022-b118e5b068dd" alt="image" width="518" />

아직 확실하게는 모르지만 `sail npm run dev`해서 실행중인 vite의 `localhost:5173`이고 실제 보여지는 뷰쪽 개발 링크가 아닌 것같다.

### Git hook 설정하기

```sh
sail pnpm add --save-dev husky
```

sail을 사용하지말고 로컬에서 구성하자.

```sh
pnpm exec husky init
```

```sh
git commit -m "Keep calm and commit"
# test script will run every time you commit
```

![image](https://github.com/Hansanghyeon/laravel-starter/assets/42893446/f5ab242b-0666-45b4-a214-c7f93f273c63)

재대로 동작한다.

## vscode tip

### Blade + Tailwind CSS IntelliSense

vscode에 Tailwind CSS IntelliSense 라는 아주 유용한 확장프로그램이있다.

그런데 blade에서 이런 곳에서는 재대로 활용할 수 없다. `<div {{ $attributes->merge(['class' => 'flex bg-red-500']) }}>TEXT</div>`

`./.vscode/settings.json`에 해당 설정을 추가하면된다.

```json
{
  "tailwindCSS.experimental.classRegex": [
    "'class' => '([^']*)", // 'class' => '...'
    "\"class\" => \"([^\"]*)", // "class" => "..."
    "'class' => \"([^\"]*)", // 'class' => "..."
    "\"class\" => '([^']*)" // "class" => '...'
  ],
  "tailwindCSS.includeLanguages": {
    "blade": "html"
  }
}
```

<img width="681" alt="image" src="https://github.com/Hansanghyeon/laravel-starter/assets/42893446/7bc81597-413c-4832-b6a9-74f037d81bd6">


## Breeze 익숙해지기

- [x] https://github.com/Hansanghyeon/laravel-guest-book
- [ ] https://youtu.be/MFh0Fd7BsjE?si=l0Z2nr-CpIQ9hho6