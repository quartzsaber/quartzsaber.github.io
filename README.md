## 개발 과정

### Ruby 설치

Jekyll은 Ruby를 사용하기 때문에 우선 ruby 개발 환경을 세팅해야 합니다.
```
# apt-get update
# apt-get install ruby-full build-essential zlib1b-dev
```

~/.bashrc에 다음 내용을 추가합니다.
```
# Install Ruby Gems to ~/gems
export GEM_HOME="$HOME/gems"
export PATH="$HOME/gems/bin:$PATH"
```

### Jekyll 설치

다음으로 Jekyll과 bundler를 설치합니다.
```
gem install jekyll bundler
jekyll new (blog path here)
```

### 깃허브 연동
깃허브 공식 가이드를 따라 깃허브와 연동시켰습니다.

우선은 `(username).github.io` 라는 이름의 레포지토리를 만들어야 합니다.
이 이름을 사용하는 레포지토리는 그 이름과 같은 웹페이지 주소로 접근했을 때 그 레포지토리의 내용을 보여줍니다.
GitHub는 Jekyll을 지원해서 Jekyll 사이트의 경우 별도의 빌드 과정 없이 푸시만 하면 자동으로 빌드된 내용이 보여집니다.

`Gemfile`을 열고 다음 내용을 넣습니다.
```
gem "jekyll"
```
로 시작하는 라인을 코멘트 처리하고 그 아래에
```
gem "github-pages", "~> 222", group: :jekyll_plugins
```
를 넣습니다.

그 다음에는
```
bundle install
```
로 방금 추가한 깃허브 플러그인을 설치합니다.
만약 이 과정에서 오류가 발생하면 `rm Gemfile.lock` 으로 버전 락 파일을 지워보는 것이 도움이 될 수 있습니다.

### Jekyll 테마
여러 테마중에 가장 깔끔해 보이는 Clean Blog 테마를 골랐습니다.

깃허브에 올리려면 remote_theme를 사용해야 합니다.

`Gemfile` 파일을 열고
```
gem "minima"
```
로 시작하는 라인을 코멘트 처리합니다.

`config.yml` 파일을 열고 `theme:`으로 시작하는 라인을
```
remote_theme: StartBootstrap/startbootstrap-clean-blog-jekyll
```
로 바꿉니다.

그 다음 커밋하고 푸시하면 `(username).github.io`에 블로그가 보이는 것을 확인할 수 있습니다.

## Posts 설정

이 테마는 Posts 페이지에 페이지 기능을 사용하기 때문에 추가 설정이 필요합니다.

`_config.yml`을 열고 

```
plugins:
  - jekyll-feed
```
가 있는 줄 바로 아래에 아래 내용을 넣습니다.

```
  - jekyll-paginate

paginate: 5
paginate_path: "/posts/page_:num"
```

## 라이선스

이 블로그의 내용은 별도로 고지되지 않는 한 <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/3.0/deed.ko">CC BY-NC-SA</a> 라이선스가 적용됩니다.

이 README.md 파일 역시 CC BY-NC-SA 가 적용됩니다.
