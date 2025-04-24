```SQL
TABLE
	author AS "Author", //보여줄 목록과 그 목록의 이름
	rating AS "Rating", //
	buy_link AS "Buy"   //
	("![["+cover+"]]") AS "Cover" //cover가 그 자체로 이미지 링크인 경우.
FROM "Books"
WHERE read = "No"
SORT year DESC
```
