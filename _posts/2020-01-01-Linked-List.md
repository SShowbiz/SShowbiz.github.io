---
layout: post
title:  "Linked List"
date:   2020-01-01
excerpt: "Linked List is the one of the enhancement of linear list"
tag:
comments: true
---

## Linked List

Linked List는 linear list를 발전시킨 선형구조 자료 형태이다.
Linear list와 다르게 element간의 연결을 이용해 list를 구현한다.
이 때 각 element는 Node라는 특별한 형태를 사용한다.

Node의 ADT는 다음과 같다.

- type data
- Node* nextNode

위의 ADT에서 data는 실제로 저장된 값의 정보이며, nextNode 는 다음 값이 저장되어 있는 Node의 주소를 가리키는 reference값이다.

Linked List의 ADT는 다음과 같다.

-  Node* head
-  Node* tail
-  int list_size
-  void insert(int position, type element)
-  void delete(int position)
-  type& get(int position)
-  int list_size()

위의 ADT에 따라 구현되는 자료의 시각적인 모습은 다음과 같다.

![linkedlist](./../assets/img/Linked_List.jpg")

그림에서 보이는 바와 같이, linear list의 기본적인 자료구조는 Node와 Node간의 연결관계를 나타내는 reference값들이다.
Node 하나당 값 하나를 포함하고 있기 때문에 Node를 추가, 제거 하면서 자유롭게 공간을 할당할 수 있다.

공간을 할당하는 방법으로는 insert와 delete 함수가 존재한다.

insert 함수를 통해 linked list의 특정 index에 element를 추가할 수 있고, delet함수를 통해 linked list의 특정부분의 element를 제거할 수 있다.
insert 함수를 통해 element가 추가되면 list_size를 1만큼 증가시켜 주어야하고, delete 함수를 통해 element가 제거되면 list_size를 1만큼 감소시켜 주어야한다.

Linear list와 다르게 Node를 이용하여 array-based implementation이 아니기 때문에 resizing 과정이 불필요하다.

## Operation Complexity

Linear list에서 제공하는 함수는 insert, delete, get, 그리고 list_size가 존재한다.

#### void insert(int position, type element)

list의 가장 특정 index에 element를 추가하는 함수이다.
단순히 다음 새로운 Node를 만들고 head부터 position 근방까지 traverse한 후에, 기존의 position-1 위치의 nextNode를 새로 만든 Node의 reference값으로, 새로 만든 Node의 nextNode를 기존의 position 위치의 Node의 reference값으로 연결시켜 주면 된다.
기존에 하던 것과 같이 element가 추가되었으므로 list_size를 1증가시킨다.
Traverse 하는 과정 때문에 O(n)의 Time complexity를 가진다.
> time complexity: O(n)

#### void delete(type element)

list의 가장 특정 index에 element를 제거하는 함수이다.
head부터 position까지 traverse한 후에, 기존의 position-1 위치의 nextNode를 기존의 position+1 위치의 Node의 reference값으로 연결시켜 주면 된다.
이 때 의미 없는 값이 들어있는 제거된 Node는 dynamic memory free를 시켜주어야 한다.
기존에 하던 것과 같이 element가 제거되었으므로 list_size를 1감소시킨다.
Traverse 하는 과정 때문에 O(n)의 Time complexity를 가진다.
> time complexity: O(n)

#### type& get(int position)
list의 특정 index에 element를 추출하는 함수이다.
head부터 position까지 traverse한 후에 그 Node에 들어있는 값을 return하면 된다.
Traverse 하는 과정 때문에 O(n)의 Time complexity를 가진다.
> time complexity: O(n)

#### int list_size()
list의 size를 resturn하는 함수이다.
private 변수인 list_size값을 return하면 된다.
> time complexity: O(1)

## Comparison with Linear List

앞서 소개해준 바에 따르면, linked list와 linear list 모두 특정 위치에서 insert와 delete가 O(n)인 것을 알 수 있다.
그렇다면, 어떤 장점이 있어서 linked list를 쓰는 것일까?

답은 간단하다. Linked list에서 insert와 remove를 할 때 parameter로 해당 node를 준다면 O(1)의 complexity로 실행이 가능하다.
또한 앞서 설명한 것 처럼 큰 array를 사용하지 않아 공간 효율성이 좋고 resizing에 시간을 쓰지 않는다.

## Application

Linked list는 다양한 응용이 가능하다.
그 예시로 유명한 것이 doubly linked list와 dummy linked list이다.
Doubly linked list는 각 Node가 뒤 Node의 reference값 뿐만 아니라 앞 Node의 reference값 또한 가지고 있는 list이다.
Dummy linked list는 head가 dummy node로, list가 0개의 data를 가진 상황에서의 insert를 if 문 없이 처리할 수 있다.
