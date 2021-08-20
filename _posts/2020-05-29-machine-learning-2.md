---
title:  "[Machine Learning] json으로 저장한 dlib 랜드마크 데이터 그래프 가시화"
excerpt: "dlib 라이브러리로 얼굴 랜드마크 데이터 python을 활용하여 가시화하기"

categories:
  - Machine Learning
tags:
  - [Machine Learning, Python, dlib]

toc: true
toc_sticky: true
 
date: 2020-05-29
last_modified_at: 2021-08-16

# sitemap :
#   changefreq : daily
#   priority : 1.0
---
![post main image](/assets/images/posts_img/machine-learning-2/ml-2-3.png)

*velog -> github 블로그로 옮기면서 동일한 게시글 업로드

종합 설계 프로젝트 기록

이전) python dlib을 활용해서 얼굴 랜드마크 검출하여 json으로 저장하는 것까지 완료했다.

먼저 관련 논문을 읽어봤다. 논문에서는 일단 시작점과의 움직임 정도로 feature을 선택했고, 추가적으로 60개 정도의 점을 더 사용했다.
-> 나도 점을 추가할 필요가 있을 것 같다. 오늘 분석해 본 결과 당연히 씹는 작용이니까 하관쪽의 움직임이 많았는데, 볼 쪽에 좀 더 점을 추가하거나, 선을 추가하면 유의미한 변화를 가진 점/선들이 좀 더 나올 것 같다. 머신러닝 좀더 찾아봐야 하는데 거기까지는 아직 못했다 ㅜ

'left.json', 'right.json'으로 왼쪽 저작 영상, 오른쪽 저작 영상을 따로 저장했다. 오늘은 저장한 데이터를 가시화하여 분석할 수 있도록 만드는데에 시간을 씀. 아래와 같은 dataframe을 만들어서 저장했다.

![dataframe](/assets/images/posts_img/machine-learning-2/ml-2-1.png)

사실 처음에는 dataframe으로 하지 않고 중첩 리스트로 만들었다. count행 68열로 만들었는데, 시각화를 하기 위해서 그림을 그리려면 dataframe을 활용해야 했고, dataframe에서 column index로 x, y축을 정하기 때문에 위와 같은 형태로 수정했다. 처음에 리스트로 구현해서 가시화 한 것이 아래 그림이다.
![dlib graph 1](/assets/images/posts_img/machine-learning-2/ml-2-2.png)


<br>dataframe으로 변경하고, column명도 추가해주고 나서 시각화시켜보았다.
변화를 수평 방향으로 나타낼 지, 수직 방향으로 나타낼 지 조금 고민했는데, box plot으로 자료가 흩어져 있는 정도를 보기 위해서는 x축을 landmark 번호로 하고, y축을 그 값으로 하는 것이 최적일 것이라고 판단했다. 자료가 흩어져 있는 정도를 보려고 한 이유는 자료가 흩어져 있다라고 하는 것은 어느 정도 움직임이 큰 것이라고 판단할 수 있다고 생각했기 때문.

>```python
sns.boxplot(x="id", y="value", hue="LR", data=landmark_df_x)
# sns.swarmplot(x="id", y="value", hue="LR", data=landmark_df_x, size = 1)
plt.xlabel('face landmarks')
plt.ylabel('coordinates')
>
plt.title('Landmarks analysis - X')
plt.legend(loc='upper right')
plt.show()
```

boxplot을 출력한 결과는 아래와 같았다.
![dlib graph 2](/assets/images/posts_img/machine-learning-2/ml-2-3.png)
![dlib graph 3](/assets/images/posts_img/machine-learning-2/ml-2-4.png)


아직 정확하게 분석해보지는 않았지만, 뭔가 딱 봤을 떄 x축 방향 보다는 y축 방향의 좌표가 흩어져 있는 정도의 차이가 크고, 내가 예상했던 하관쪽에서의 움직임이 발생한 것을 볼 수 있었다.

![dlib facial landmarks](/assets/images/posts_img/machine-learning-2/ml-2-5.png)


5-12(턱 쪽), 50~60(입) 쪽 변화가 확연하게 큰게 보인다. 근데 49~67, 즉 입쪽에서 왼쪽 부분의 변화가 적은데 이게 내가 씹는 것에 문제가 있는 건지 뭔지 모르겠다..

<br>* 논문에서는 점 하나하나의 좌표값의 변화 말고 그룹핑한 변화로 판단하더라. 그렇게도 한번 해봐야겠다.