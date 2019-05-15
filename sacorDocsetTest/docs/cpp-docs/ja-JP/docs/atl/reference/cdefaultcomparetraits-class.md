---
title: CDefaultCompareTraits クラス
ms.date: 11/04/2016
f1_keywords:
  - CDefaultCompareTraits
  - 'ATLCOLL/ATL::CDefaultCompareTraits'
  - 'ATLCOLL/ATL::CDefaultCompareTraits::CompareElements'
  - 'ATLCOLL/ATL::CDefaultCompareTraits::CompareElementsOrdered'
helpviewer_keywords:
  - CDefaultCompareTraits class
ms.assetid: a17e2740-e7b4-48f2-aeb7-c80ce84b63f7
---
# <a name="cdefaultcomparetraits-class"></a>CDefaultCompareTraits クラス

このクラスは、既定の要素の比較関数を提供します。

## <a name="syntax"></a>構文

```
template<typename T>
class CDefaultCompareTraits
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
コレクションに格納されるデータの型。

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CDefaultCompareTraits::CompareElements](#compareelements)|(静的)2 つの要素が等しいかどうかを比較するには、この関数を呼び出します。|
|[CDefaultCompareTraits::CompareElementsOrdered](#compareelementsordered)|(静的)この関数では、大小の要素を決定します。|

## <a name="remarks"></a>Remarks

このクラスには、コレクション クラスのオブジェクトに格納されている要素を比較するための 2 つの静的関数が含まれています。 このクラスは、によって使用されて、 [CDefaultElementTraits クラス](../../atl/reference/cdefaultelementtraits-class.md)します。

詳細については、次を参照してください。 [ATL コレクション クラス](../../atl/atl-collection-classes.md)します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcoll.h

##  <a name="compareelements"></a>  CDefaultCompareTraits::CompareElements

2 つの要素が等しいかどうかを比較するには、この関数を呼び出します。

```
static bool CompareElements(const T& element1, const T& element2);
```

### <a name="parameters"></a>パラメーター

*element1*<br/>
1 番目の要素。

*element2*<br/>
2 番目の要素。

### <a name="return-value"></a>戻り値

要素が false でそれ以外の場合、等しい場合は true を返します。

### <a name="remarks"></a>Remarks

この関数の既定の実装は、等しいかどうか ( **==** ) 演算子。 単純なデータ型以外のオブジェクト、この関数は、オーバーライドする必要があります。

##  <a name="compareelementsordered"></a>  CDefaultCompareTraits::CompareElementsOrdered

この関数では、大小の要素を決定します。

```
static int CompareElementsOrdered(const T& element1, const T& element2);
```

### <a name="parameters"></a>パラメーター

*element1*<br/>
1 番目の要素。

*element2*<br/>
2 番目の要素。

### <a name="return-value"></a>戻り値

次の表に基づく整数を返します。

|条件|戻り値|
|---------------|------------------|
|*element1* < *element2*|< 0|
|*element1* == *element2*|0|
|*element1* > *element2*|>0|

### <a name="remarks"></a>Remarks

この関数の既定の実装を使用して、 **==** 、 **\<** 、および **>** 演算子。 単純なデータ型以外のオブジェクト、この関数は、オーバーライドする必要があります。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)
