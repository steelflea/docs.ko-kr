---
title: Fixed 키워드 (F#)
description: 고정할 수 있으므로' ' 하는 방법으로 스택에 F#을 사용 하 여 컬렉션을 방지 하기 위해 로컬 'fixed' 키워드에 알아봅니다.
ms.date: 04/24/2017
ms.openlocfilehash: 1bf1b2ad67d2dd7f854e569cfca7c06e8aec7f4c
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/02/2018
ms.locfileid: "45624511"
---
# <a name="the-fixed-keyword"></a>Fixed 키워드

F# 4.1 소개를 `fixed` "고정" 스택에 로컬 수집 되거나 가비지 수집 하는 동안 이동 하지 못하게 할 수 있는 키워드입니다.  하위 수준 프로그래밍 시나리오에 사용 됩니다.

## <a name="syntax"></a>구문

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a>설명

이 확장에 대 한 포인터를 추출 하 고 수집 되거나 가비지 컬렉션 도중 이동 못하게 하는 이름에 바인딩할 수 있도록 식의 구문입니다.  

식에서 포인터를 통해 고정 되어는 `fixed` 키워드를 통해 식별자에 바인딩되는 `use` 키워드입니다.  리소스 관리를 통해이 의미 체계가 비슷합니다는 `use` 키워드입니다.  포인터는 범위에는 더 이상 고정 범위를 벗어납니다 있으면 하는 동안 고정 됩니다.  `fixed` 컨텍스트 외부에서 사용할 수 없습니다는 `use` 바인딩.  사용 하 여 이름으로 포인터를 바인딩해야 `use`합니다.

사용 `fixed` 함수 또는 메서드의 식 내에서 발생 해야 합니다.  스크립트 또는 모듈 수준의 범위에서 사용할 수 없습니다.

모든 포인터 코드와 같은 안전 하지 않은 기능은이 및에서 사용 하는 경우 경고를 생성 합니다.

## <a name="example"></a>예제

```fsharp
open Microsoft.FSharp.NativeInterop

type Point = { mutable X: int; mutable Y: int}

let squareWithPointer (p: nativeptr<int>) =
    // Dereference the pointer at the 0th address.
    let mutable value = NativePtr.get p 0

    // Perform some work
    value <- value * value

    // Set the value in the pointer at the 0th address.
    NativePtr.set p 0 value

let pnt = { X = 1; Y = 2 }
printfn "pnt before - X: %d Y: %d" pnt.X pnt.Y // prints 1 and 2

// Note that the use of 'fixed' is inside a function.
// You cannot fix a pointer at a script-level or module-level scope.
let doPointerWork() =
    use ptr = fixed &pnt.Y

    // Square the Y value
    squareWithPointer ptr
    printfn "pnt after - X: %d Y: %d" pnt.X pnt.Y // prints 1 and 4

doPointerWork()
```

## <a name="see-also"></a>참고자료

- [NativePtr 모듈](https://msdn.microsoft.com/visualfsharpdocs/conceptual/nativeinterop.nativeptr-module-%5Bfsharp%5D)
