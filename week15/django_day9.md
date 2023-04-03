## HTML form

- 사용자로부터 form 요소를 통해 데이터를 받고 있으나, 비정상적 혹은 악의적 요청을 확인하지 않고 모두 수용중
- 우리가 원하는 데이터 형식이 맞는지에 대한 유효성 검증 필요

## 유효성 검사

- 수집한 데이터가 정확하고 유효한지 확인하는 과정
- 유효성 검증에는 입력값, 형식, 중복, 범위, 보안 등 부가적인 많은 것들을 고려
- 이런 과정과 기능을 제공해주는 도구 필요

## Django Form

- 사용자 입력 데이터를 수집하고 처리 및 유효성 검증을 수행하기 위한 도구
- 유효성 검사를 단순화하고 자동화할 수 있는 기능 제공

### Form class 선언

- forms.py 파일 생성
- `from django import forms` 를 통해 forms 모듈 import
- 아래와 같이 model 생성과 비슷한 방법을 통해 클래스 생성
    
    ```python
    class ArticleForm(forms.Form):
    	title = forms.CharField(max_length=10)
    	content = forms.CharField()
    ```
    

### 새로운 form class 적용

- views.py에 아래와 같이 form 클래스를 context로 전달

```python
def new(request):
	form = ArticleForm()
	context = {
		'form': form,
	}
	return render(request, 'articles/new.html', context)
```

- new.html에 있던 기존의 form 태그를 `{{ form }}` 으로 변경
    - `{{ form.as_p }}` 를 통해 p 태그로 감쌀 수 있음

### widget 적용

- input 요소의 속성 및 출력되는 부분을 변경하는 것
- `content = forms.CharField(widget=forms.Textarea)`와 같이 여러 가지의 input 방식을 지정 가능

## Django ModelForm

### Form vs ModelForm

- Form: 사용자 입력 데이터를 DB에 저장하지 않을 때 사용 (ex. 로그인)
- ModelForm: 사용자 입력 데이터를 DB에 저장해야 할 때 사용 (ex. 회원가입)

### Meta class

- ModelForm 의 정보를 작성하는 곳
- 기존 Form 클래스 변경
    
    ```python
    class ArticleForm(forms.ModelForm):
    	class Meta:
    		model = Article   # 기존 model 재사용
    		fields = '__all__'
    ```
    
- fields 변수에 사용자 입력이 필요한 필드 지정 가능
    - ex. `fields = ('title', )`와 같이 작성하면 title 만 입력하도록 구현됨
    - exclude 변수에 작성하면 해당 필드를 제외한 필드를 입력하도록 구현됨

### ModelForm을 적용한 views.py 작성

- create
    
    ```python
    def create(request):
    	form = ArticleForm(request.POST)
    	if form.is_valid():    # 유효성 검사 통과 시
    		article = form.save()
    		return redirect('articles:detail', article.pk)
    
    	# 유효성 검사 통과 못할 시
    	context = {
    		'form': form,
    	}
    	return render(request, 'articles/new.html', context)
    
    ```
    
    - `is_valid()`
        - 여러 유효성 검사를 실행하고 데이터가 유효한지 여부를 boolean 형태로 반환
- edit
    
    ```python
    def edit(request, article_pk):
    	article = Article.objects.get(pk=article_pk)
    	form = ArticleForm(instance=article)    # 인자로 기존 객체를 전달
    	context = {
    		'article': article,
    		'form': form,
    	}
    	return render(request, 'articles/edit.html', context)
    ```
    
    - edit.html의 form 태그 내부도 `{{ form.as_p }}` 과 같이 변경
- update
    
    ```python
    def update(request, pk):
    	article = Article.objects.get(pk=pk)
    	form = ArticleForm(request.Post, instance=article)
    	if form.is_valid():
    		form.save()
    		return redirect('articles:detail', article.pk)
    	context = {
    		'form': form,
    		'article': article,
    	}
    	return render(request, 'articles/edit.html', context)
    ```
    

## Django HTTP request handling

- 예시의 new, create 함수를 결합
    - HTTP Method에 따라 기존 결합 전의 new, create 함수가 동작