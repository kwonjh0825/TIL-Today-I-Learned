## ORM Update, Delete

- Update
    - 인스턴스 조회 후 변수 변경, 저장
    
    ```python
    article = Article.objects.get(pk=1)
    article.title = 'hi'
    article.save()
    ```
    
- Delete
    - 삭제 할 인스턴스 조회 후 delete 메서드 호출
    - 삭제 된 객체가 반환됨
    
    ```python
    article = Article.objects.get(pk=1)
    article.delete()
    ```