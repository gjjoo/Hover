# Hover
Sass를 위한 Hover Custom 자료입니다.<br>
hover 라이브러리에서 Sass부분을 보완한 자료입니다.

```
Hover: https://github.com/IanLunn/Hover
```
<br>

기존에는 클래스포함여부 상관없이 모든 키프레임을 CSS로 출력하게끔 되어 있었습니다. 사용한 Mixin의 keyframe만 출력하게 하고 중복으로 사용시에도 keyframe이 한번 만 출력되게끔 수정했습니다.
```sass
/* Buzz */
$hover-buzz: true; /* Add */
@mixin buzz {
  @include hacks();

  &:hover,
  &:focus,
  &:active {
    @include prefixed(animation-name, #{$nameSpace}-buzz);
    @include prefixed(animation-duration, .15s);
    @include prefixed(animation-timing-function, linear);
    @include prefixed(animation-iteration-count, infinite);
  }
  @if $hover-buzz { /* Add */
    $hover-buzz: false !global; /* Add */
    @include keyframes(#{$nameSpace}-buzz) {
      50% {
        @include prefixed(transform, translateX(3px) rotate(2deg));
      }

      100% {
        @include prefixed(transform, translateX(-3px) rotate(-2deg));
      }
    }
  }
}
```
<br>

`pulse`와 `push` 파일이 `animtewithsass` 라이브러리와 중복되어 이름을 수정하였습니다.
```sass
  /* 기본 파일 */
  @include hvr-pulse();
  @include hvr-push();
```

```sass
  /* 수정된 파일 */
  @include hvr-pulse();
  @include hvr-push();
```