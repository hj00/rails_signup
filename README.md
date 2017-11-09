### 4일차

1. Static Website ex) Landing Page
2. Dynamic Website ex) Twitter, Facebook



### Ruby

> 변수 이름
>
> 1. 소문자로 시작  My_age(x)
>
> 2. 단어들은 _(underscore)로 구분 : snakecase  myAge(x)
>
> 3. {}, '@' 등의 기호들로 시작하지 말자 $my_age(x)
>
> 4. Data 종류 - Symbol ex) :name
>
>    > String과 같다고 생각하면 이해하기 쉬움. 메모리에 영구적인 장소를 차지(한 번 지정되면 변하지 않음.)
>    >
>    > 주로 함수 이름, 키 이름, 변수 등의 ID로 사용된다. ex) student[:grade]
>
> 5. Data 종류 - Array
>
> 6. Data 종류 - Hash  : key값으로 strin, symbol 모두 쓸 수 있지만 가능한 symbol 쓰는게 좋다..?
>
>    > ex)
>    >
>    > ```ruby
>    > order = {"item" => "Corn Flakes", "weight" => 18}
>    >
>    > order = {:item => "Corn Flakes", "weight" => 18}
>    >
>    > order = {item: "Corn Flakes", "weight" => 18} == 2)와 같은 의미.
>    > ```

### rails CRUD

#### rails g(enerate) controller uyser

1. routes
2. controller
3. view

#### rails g model user

- t.string :email
- t.string :password
- rake db:migrate

#### 회원가입

0. (root)user/index => 모든 유저정보를 나열해준다.
   - 회원가입 링크, 각각의 회원 정보 옆에는 수정&삭제 링크


1. usernew => 회원가입페이지 form
2. user/create => 회원가입완료
3. user/modify/:id => 자신의 정보를 수정하는 페이지
4. user/update => 수정완료
5. user/destroy/:id => 유저정보삭제

### 로그인

0. 로그인으로 받아온 정보의 유저가 DB에 있는지 확인?

```ruby
params[:email]
if User.exists? (email: params[:email])
	user = User.find_by(email: params[:email])
	if user.password == Digest::MD5.hexdigest(params[:password])
      session[:user_id] = user.id
      redirect_to '/'
    end
end
```

1. 만약에 있다면, 비밀번호가 맞는지 확인?
2. 그것도 만약에 맞다면, 로그인 시키기



## 따라가기

rails destroy controller user(=rails d controller user) : 생성된 것 제거

#### in command

rails g(enerate) controlleer user index new create modify update destroy # action미리 선언

#### In routes.rb

root 'user#index'  # get '/' => '/user/index'와 동일한 기능

-> create.erb 까지 생성



#### In command

rails g model user

#### db>>migrate>>201711_create_users.rb

위 파일에 필요 칼럼 추가 

t.string: email

t.string: password



#### Gemfile

group :development do의 맨 마지막에

gem 'rails_db' 입력

-> terminal창에서 bundle install



ruby에서 md5 사용

콘솔 창에서

irb

require 'digest'

Digest::MD5.hexdigest('123')





### 세션(Session)

cf) 쿠키 : 서버가  내 PC에 기억시키는 것. 서버가 내 PC에 

세션은(session_store.rb)파일에서 기간을 설정

Ruby on rails에서 세션은 해쉬처럼, 쿠키는 객체처럼 사용????





