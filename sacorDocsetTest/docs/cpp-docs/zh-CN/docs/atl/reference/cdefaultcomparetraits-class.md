---
title: CDefaultCompareTraits 类
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
# <a name="cdefaultcomparetraits-class"></a>CDefaultCompareTraits 类

此类提供了默认元素比较函数。

## <a name="syntax"></a>语法

```
template<typename T>
class CDefaultCompareTraits
```

#### <a name="parameters"></a>参数

*T*<br/>
要存储在集合中的数据类型。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CDefaultCompareTraits::CompareElements](#compareelements)|（静态）调用此函数可比较两个元素相等性。|
|[CDefaultCompareTraits::CompareElementsOrdered](#compareelementsordered)|（静态）调用此函数可确定的更高版本或较低的元素。|

## <a name="remarks"></a>备注

此类包含用于比较集合类对象中存储的元素的两个静态函数。 使用此类[CDefaultElementTraits 类](../../atl/reference/cdefaultelementtraits-class.md)。

有关详细信息，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。

## <a name="requirements"></a>要求

**标头：** atlcoll.h

##  <a name="compareelements"></a>  CDefaultCompareTraits::CompareElements

调用此函数可比较两个元素相等性。

```
static bool CompareElements(const T& element1, const T& element2);
```

### <a name="parameters"></a>参数

*element1*<br/>
第一个元素。

*element2*<br/>
第二个元素。

### <a name="return-value"></a>返回值

如果元素均相等，则返回 false，则返回 true。

### <a name="remarks"></a>备注

此函数的默认实现是等号 ( **==** ) 运算符。 对于不属于简单的数据类型的对象，此函数可能需要重写。

##  <a name="compareelementsordered"></a>  CDefaultCompareTraits::CompareElementsOrdered

调用此函数可确定的更高版本或较低的元素。

```
static int CompareElementsOrdered(const T& element1, const T& element2);
```

### <a name="parameters"></a>参数

*element1*<br/>
第一个元素。

*element2*<br/>
第二个元素。

### <a name="return-value"></a>返回值

返回一个整数，基于以下表：

|条件|返回值|
|---------------|------------------|
|*element1* < *element2*|<0|
|*element1* == *element2*|0|
|*element1* > *element2*|>0|

### <a name="remarks"></a>备注

此函数的默认实现使用 **==** ， **\<** ，以及 **>** 运算符。 对于不属于简单的数据类型的对象，此函数可能需要重写。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
