---
layout: post
title: "Unix 명령어 특집 1 - Directory"
date: 2021-09-12 23:47:46 +0900
categories: jekyll update
tags: unix command cd
---

## Directory

우리는 개발을 공부하면서 여러 프로젝트를 만들 수 있다. 이때, 프로젝트별로 `Directory` 를 관리해주어야 내가 하고 있는 프로젝트가 다른 프로젝트와 겹치지 않을 수 있다. 그렇다면 우리는 이러한 `Directory` 를 어떠한 방식으로 관리해주어야 할까? 오늘은 이 `Directory` 를 확인하고 움직이는 과정에 대해 알아볼 예정이다.

# Directory의 기본 구조 (Structure of Directory)

`Directory` 는 작업 공간을 의미한다. 이때, 작업공간은 단순히 Code를 작성하는 공간에 의미를 넘어서, 나의 여러 사진을 저장하는 공간, 나의 음악을 저장하는 공간등 내가 노트북 혹은 컴퓨터를 사용하면서 특수한 목적을 위해 생성한 작업 공간이다. 필자가 사용하고 있는 Mac OS X의 기본 `Directory` 는 다음과 같다.

{% highlight zsh %}
$ ls -l // 이는 추후 다룰 명령어 이다. (현재 Directory의 구조를 보여주는 명령어다.)

> drwxr-xr-x+ 62 junsu staff 1984 9 13 01:33 .
> drwxr-xr-x 5 root admin 160 8 15 13:28 ..
> drwxr-xr-x 5 junsu staff 160 8 19 15:58 Applications
> drwx------+ 36 junsu staff 1152 9 12 23:31 Desktop
> drwxr-xr-x 13 junsu staff 416 9 12 01:08 Developer
> drwx------+ 3 junsu staff 96 8 15 13:28 Documents
> drwx------+ 16 junsu staff 512 9 11 22:51 Downloads
> drwx------@ 74 junsu staff 2368 9 10 14:36 Library
> drwx------ 3 junsu staff 96 8 15 13:28 Movies
> drwx------+ 4 junsu staff 128 8 15 15:56 Music
> drwx------+ 4 junsu staff 128 8 15 13:29 Pictures
> drwxr-xr-x+ 4 junsu staff 128 8 15 13:28 Public
> drwxr-xr-x 8 junsu staff 256 9 10 12:25 Study
> drwxr-xr-x 3 junsu staff 96 8 17 14:57 opt
> {% endhighlight %}

- `.` 은 현재 위치한 `Directory` 라는 `Directory` 이다. (조금 헷갈릴 수 있는 개념)
- `..`은 현재 위치한 `Directory` 의 직전 `Directory` 이다.
- `Applications` 는 Mac 에서 사용하는 여러 프로그램이 담겨있는 `Directory` 이다.
- `Desktop` 은 사용자의 바탕화면을 구성하는 `Directory` 이다.
- `Developer` 는 여러 개발 공부를 위해 필자가 따로 생성한 `Directory` 이다.
- `Documents` 는 여러 문서를 저장하기 위한 `Directory` 이다.

다음과 같이 Mac OS X 에서는 사용자를 생성할 경우 자동으로 여러 `Directory` 를 생성해준다. 그렇다면 우리는 이러한 `Directory` 를 어떻게 생성하고, 어떻게 삭제하며, 어떻게 이동할지에 대하여 배워보자.

# 새로운 Directory를 생성해줘(Make Directory)

{% highlight zsh %}
$ mkdir directory
{% endhighlight %}

mkdir은 MakeDirectory의 약자로 새로운 `Directory` 를 생성해달라는 명령어이다. 내가 새로운 작업공간을 만들고 싶다면 mkdir DirectoryName 을 입력하면 새로운 `Directory`를 생성해 준다.

# Directory를 삭제하고 싶어(Remove Directory)

{% highlight zsh %}
$ rmdir directory
{% endhighlight %}

rmdir은 RemoveDirectory의 약자로 존재하고 있는 `Directory`를 삭제해달라는 명령어이다. 만약 내가 현재 작업하고 있는 공간이 더이상 필요하지 않다면, rmdir DirectoryName 을 입력하여 `Directory` 를 삭제하자. 이때, 삭제하고 싶은 `Directory` 는 무조건 비어있어야 한다. 만약 `Directory` 가 비어있지 않지만, 그럼에도 불구하고 삭제하고 싶다면 다음과 같이 입력해보자.

{% highlight zsh %}
$ rm -rf directory
{% endhighlight %}

이는 후에 배울 명령어 중 하나인데 `File` 을 삭제하는데 사용되는 명령어 중 하나이다. `Directory`를 Remove 하되, -r(하위 모든 `Directory` 및 `File` 포함), -f (권한에 상관없이) 제거해달라는 명령어이다. 지금은 간단히만 이해하고 넘어가자.

# 현재 위치를 찾아줘(Print Working Directory)

{% highlight zsh %}
$ pwd

> /home/junsu
> {% endhighlight %}

pwd는 PrintWorkingDirectory의 약자로 현재 `Directory` 를 알려달라는 명령어이다. 내가 현재 작업하고 있는 `Directory` 가 어디인지 모를 때, pwd 라는 명령어를 입력하면 현재 내 위치를 반환해 준다.

# 내 위치를 변경해줘(Change Directory)

{% highlight zsh %}
$ cd
{% endhighlight %}

cd 는 ChangeDirectory의 약자로 `Directory` 를 이동해달라는 명령어이다. cd 뒤에는 이동할 `Directory` 를 적으면 해당하는 `Directory` 로 이동할 수 있게 된다.

만약 우리가 `Project` 라는 `Directory` 로 이동하고 싶다면 다음과 같이 작성하면 된다.

{% highlight zsh %}
$ cd Project
{% endhighlight %}

# 특수한 위치로 가고싶어(SpecialCase)

{% highlight zsh %}
$ cd .
$ cd ..
$ cd ~
$ cd /
{% endhighlight %}

위에서 나온 커맨드는 이동할 `Directory` 를 입력하지 않고도 특수한 위치로 이동할 수 있게 해주는 명령어이다. 하나씩 살펴보자.

- `cd .` 현재 `Directory` 를 의미하며, 현재 위치로 이동하라는 명령어다. 사실상 무의미 하다.
- `cd ..` 현재 `Directory` 의 직전 `Directory` 를 의미하며, 직전 위치로 이동하라는 명령어다.
- `cd ~` 현재 로그인된 사용자의 `Home` 를 의미하며, 로그인 사용자의 Home 으로 이동하라는 명령어다.
- `cd /` OS가 설치된 가장 최상단 위치를 의미하며, `Directory` 의 최상단 으로 이동하라는 명령어다.
