깨진 이미지 복구하기 문제이다.
주어진 png 파일을 열어보면 플래그가 일부만 보이고 짤려져 있다.

원래는 정사각형이었다는 힌트가 있다.

HxD로 파일을 열어보면 IHDR 청크의 값이 다음과 같다.
```
00 00 02 00 00 00 01 00
```

512 x 256 픽셀 크기라는 뜻이므로, 아래와 같이 수정한다.
```
00 00 02 00 00 00 02 00
```

그럼 이미지를 복구할 수 있다.

### PNG IHDR 청크
시그니처 바로 뒤 4바이크가 IHDR 청크의 크기이다.
89 50 4E 47 0D 0A 1A 0A 00 00 00 0D 49 48 44 52 00 00 02 00 00 00 02 00
IHDR 청크의 태그 값은 49 48 44 52 이며, 태그 값 뒤에 크기 값이 나온다.
