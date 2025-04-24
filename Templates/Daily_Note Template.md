---
date_daily: <% tp.file.title.slice(0, 10) %>
achievement: 
emotion: 
income: 0
expense: 0
important_date: false
tags:
  - daily
---
<%*
    const currentMoment = moment(tp.file.title, "YYYY-MM-DD");
    tR += '❮ ';
	tR += '[[' + currentMoment.format('YYYY|YYYY년') + ']]' + ' / ';
	tR += '[[' + currentMoment.format('YYYY-MM|MM월') + ']]' + ' / ';
	tR += '[[' + currentMoment.format('gggg-[W]ww') + '|' + currentMoment.format('ww[주]') + ']]';
	tR += ' ❯';
	tR += '\n';
    tR += '❮❮ ';
    currentMoment.add(-1,'days');
    tR += '[[' + currentMoment.format('YYYY-MM-DD(ddd)') + ']]' + ' | ';
    currentMoment.add(1,'days');
    tR += currentMoment.format('YYYY-MM-DD(ddd)') + ' | ';
    currentMoment.add(1,'days');
    tR += '[[' + currentMoment.format('YYYY-MM-DD(ddd)') + ']]';
    currentMoment.add(-1,'days');
    tR += ' ❯❯';
%>

---

## 오늘 되짚을 일
<%*
    let yesterday = "10. Diary/1. Daily/" + tp.date.now("YYYY-MM-DD(ddd)", -1, tp.file.title, "YYYY-MM-DD(ddd)");
    let section = "## 내일 떠올릴 일";
    let should_include = false;
    let sectionContent = "";

    let yfile = tp.file.find_tfile(yesterday);
    if (yfile) {
        const content = await app.vault.read(yfile);
        if (content.includes(section)) {
            let startIndex = content.indexOf(section) + section.length;
            let endIndex = content.indexOf('---', startIndex);
            endIndex = endIndex === -1 ? content.length : endIndex;
            sectionContent = content.substring(startIndex, endIndex).trim();
            should_include = sectionContent.length > 0;
        }
    }

	const nothing_to_do = "- ❌ 오늘 되짚을 일이 없습니다.";
    tR += should_include ?
	    (sectionContent.includes("- 내일 떠올릴 일을 적어주세요.") ?
		    nothing_to_do :
			sectionContent) :
		nothing_to_do;
%>

## 내일 떠올릴 일
- 내일 떠올릴 일을 적어주세요.

---
## 일기 본문
일기의 내용을 적어주세요.

## 성찰 질문
> [!Q : 여기에 성찰 질문을 적어주세요]
> A

## AI의 성찰 리뷰
AI의 성찰 리뷰가 들어갈 자리입니다.

---
### 오늘 끝내야 하는 일
```tasks
due on or before <% tp.file.title.slice(0,10) %>
filter by function task.file.folder.includes("10. Planner")
filter by function !task.file.folder.includes("templates")
not done
sort by priority
```

### 못다한 과제
```tasks
tag include #과제
not done
sort by priority
```

### 반복 할 일
<%*
let today = moment(tp.file.title, "YYYY-MM-DD").format("YYYY-MM-DD");
tR += "- [ ] 영어독립 공부 ⏫ ⏳ " + today;
tR += '\n';
tR += "- [ ] 한경신문 읽기 🔼 ⏳ " + today;
%>

### 언젠가 할 일
```tasks
no due date
not done
scheduled date is invalid

is not recurring
description regex does not match /^$/
path does not include Templates
```

### 할 일 추가하기
- ❗할 일 추가하기
