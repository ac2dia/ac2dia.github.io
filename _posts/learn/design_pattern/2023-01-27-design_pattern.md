---
title: 'Singleton in creational Pattern'

categories:
  - DesignPattern
tags:
  - [CreationalPatterns]

toc: true
toc_sticky: true

date: 2023-01-27
last_modified_at: 2023-01-27
---

# Singleton
생성 디자인 패턴이며, 클래스 당 하나의 인스턴스만 보장하는 전략입니다.

## Problem
1. 클래스는 오직 하나의 인스턴스만을 가지도록 보장합니다.
    - 주로 공유 자원에 대한 접근을 제어하기 위해 사용 (데이터베이스, 파일 ...)

2. 인스턴스에 전역 접근 포인트를 제공합니다.

## Solution
1. 다른 오브젝트에서 싱글톤 클래스의 new operator 를 사용하는 것을 방지하기 위해, private 접근 제한자를 가진 기본 생성자를 작성합니다.
2. 생성자와 같은 역할을 하는 static 메서드를 생성합니다. 

## Real-World Analogy
현실 세계에서는 정부와 같은 기관이 싱글톤 클래스의 대표적인 예입니다. 한 국가에서 공식적으로는 하나의 정부만 존재하기 때문입니다.

## Structure
![싱글톤 클래스 구조](/assets/images/learn/design_pattern/2023-01-27%20Singleton%20Structure.png)
1. 동일한 인스턴스를 반환하는 getInstance() 라는 이름의 static 메서드를 선언합니다.
2. 싱글톤 클래스의 생성자는 외부로 제공되지 않아야 합니다. 오직 getInstance() 메서드만이 인스턴스에 접근할 수 있는 접근 포인트입니다.

## Psudocode
``` java
// The Database class defines the `getInstance` method that lets
// clients access the same instance of a database connection
// throughout the program.
class Database is
    // The field for storing the singleton instance should be
    // declared static.
    private static field instance: Database

    // The singleton's constructor should always be private to
    // prevent direct construction calls with the `new`
    // operator.
    private constructor Database() is
        // Some initialization code, such as the actual
        // connection to a database server.
        // ...

    // The static method that controls access to the singleton
    // instance.
    public static method getInstance() is
        if (Database.instance == null) then
            acquireThreadLock() and then
                // Ensure that the instance hasn't yet been
                // initialized by another thread while this one
                // has been waiting for the lock's release.
                if (Database.instance == null) then
                    Database.instance = new Database()
        return Database.instance

    // Finally, any singleton should define some business logic
    // which can be executed on its instance.
    public method query(sql) is
        // For instance, all database queries of an app go
        // through this method. Therefore, you can place
        // throttling or caching logic here.
        // ...

class Application is
    method main() is
        Database foo = Database.getInstance()
        foo.query("SELECT ...")
        // ...
        Database bar = Database.getInstance()
        bar.query("SELECT ...")
        // The variable `bar` will contain the same object as
        // the variable `foo`.
```

# 참고 문헌
[1] Singleton, https://refactoring.guru/design-patterns/singleton <br>