---
title: React란?
author: Luke
date: 2022-07-06 10:01:00 +0900
categories: [Web, React]
tags: [react]
---

*이번 포스트에서는 리액트란 무엇인지 알아보고 프로젝트를 생성하는 것 까지를 다루겠습니다*

# React?

공식적으로 리액트는 사용자 인터페이스를 만들기 위한 라이브러리 입니다. 리액트는 프레임워크가 아니며, 심지어 웹에서만 사용할 수 있는 것도 아닙니다.  
리액트는 다른 라이브러리들과 함께 특정 환경을 렌더링하는 데 사용됩니다.  

예를 들면, 웹 환경에서는 React, 모바일 환경에서는 React-Native, VR 환경은 React 360을 사용하여 구현이 가능합니다.

> React360의 경우 2020년 이후 PR, Issue 등이 업데이트되지 않고 있습니다.
> 아무래도 VR을 구현하기에 좋은 프레임워크가 많기 때문이라 추측됩니다.
{: .prompt-warning }

웹을 만들 때는 ReactDOM과 함께 사용합니다. `React + ReactDOM`은 Vue와 같은 프레임워크와 동일한 문제를 해결하기 위해 사용됩니다.

# React의 사용

NextJS와 같은 프레임워크와 달리, 리액트는 코드 컨벤션이나 파일 구조에 엄격한 규칙을 가지지 않습니다.  
즉, 리액트로 구현할 수 있는 범위는 자유로워서, 하나의 버튼, 인터페이스의 일부분, 심지어는 애플리케이션의 전체를 구현할 수도 있습니다.  

> 대부분의 프레임워크나 JQuery 라이브러리와 달리, 다른 프레임워크나 라이브러리로 구현된 프로젝트에 리액트로 구현된 코드를 이식하는 것이 매우 어렵습니다.
> 리액트는 애플리케이션 전체를 구현할 때 사용하는 것이 쉬운 접근 방법입니다.
{: .prompt-info }

리액트를 시작하는 방법은 React, ReactDOM 및 필요한 구성 요소를 직접 구성하는 방법과 `create-react-app(CRA)`를 사용하는 방법 두 가지가 있습니다.  
이번 포스트에서는 `CRA`를 이용하여 프로젝트를 생성하는 것 까지 알아보도록 하겠습니다.

# 필요한 환경

## Node.js

CRA를 사용하기 위해서는 `Node.js`가 필수적으로 필요합니다.  
Node.js 버전은 LTS(Long-Term Support) 버전을 사용하는 것을 추천합니다. 안정적이며 오래 지원하기 때문이죠.  

> 2022.07.06 기준 LTS 버전은 16.15.1 이며
> 다운로드 링크는 [Node.js Download](https://nodejs.org/ko/download/) 입니다.  
> 해당 포스트에서는 Node.js 설치 방법을 설명하지는 않습니다. 필요하다고 판단되면 추후 다른 포스트에서 다루겠습니다.
{: .prompt-info }

Node.js를 설치하게 되면 npx, npm이 함께 설치되는데, 간단하게 알아보도록 하겠습니다.

### npm

NPM은 `Node Package Manager`의 약자로 npm repository에서 패키지를 다운로드할 수 있으며, 이러한 모듈들을 npm script에 명시하여 프로젝트의 
Node 모듈을 관리하는 역할을 수행합니다.

아래의 명령어와 같이 사용되며, 실행 후 프로젝트 root에 node_modules 라는 폴더가 생성되어 관리하게 됩니다.

```bash
# dependency
npm install $PACKAGE_NAME

# devDependency
npm install $PACKAGE_NAME --save-dev
```
{: .nolineno }

`dependency` 및 `devDependency`의 경우 추후 package.json에 대한 포스트에서 다루도록 하겠습니다.

> NPM과 비슷한 역할의 패키지 매니저인 YARN이 있습니다.
{: .prompt-info }

### npx

시스템 전역적으로 Node 모듈을 설치하여 사용해야할 때, 과거에는 다음과 같이 전역에 Node 모듈을 설치하여 실행했습니다.

```bash
# -g -> Global option
npm install $PACKAGE_NAME -g
```
{: .nolineno}

이러한 방법은 여전히 유용하지만, 일시적으로 사용하는 모듈을 매번 로컬에 설치하는 것은 곧 공간의 낭비로 이어집니다.  
npm 5.2 버전부터 `npx`라는 도구를 지원합니다.  
간단하게 설명하면 Node 모듈을 임시로 설치하여 실행하고, 실행 후 자동으로 fallback 되어 패키지는 사라지게 됩니다.  

로컬 전역에 사용될 node_modules 폴더를 관리할 필요도 없고 공간을 절약할 수 있음을 알 수 있습니다.

# 프로젝트 생성

환경에서 살펴본 npx를 이용하여 프로젝트를 생성하겠습니다.

```bash
npx create-react-app $PROJECT_NAME
```
{: .nolineno }

위의 명령어를 수행하면 기본적인 리액트 프로젝트가 생성됩니다.

# 마무리

다음 포스트에서는 리액트 프로젝트의 구조와 관리에 대해서 작성하도록 하겠습니다.