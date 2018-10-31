---
title: _bstr_t::operator += + | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::operator+
- _bstr_t::operator+=
dev_langs:
- C++
helpviewer_keywords:
- += operator [C++], appending strings
- + operator [C++], _bstr_t objects
ms.assetid: d28316ce-c2c8-4a38-bdb3-44fa4e582c44
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a440e8b8d078c7849de2a0b29f1d50b140d70070
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044775"
---
# <a name="bstrtoperator--"></a><span data-ttu-id="ff21d-102">_bstr_t::operator +=, +</span><span class="sxs-lookup"><span data-stu-id="ff21d-102">_bstr_t::operator +=, +</span></span>

<span data-ttu-id="ff21d-103">**Microsoft'a özgü**</span><span class="sxs-lookup"><span data-stu-id="ff21d-103">**Microsoft Specific**</span></span>

<span data-ttu-id="ff21d-104">Sonuna karakterler ekler `_bstr_t` nesne veya iki dizeyi art arda ekler.</span><span class="sxs-lookup"><span data-stu-id="ff21d-104">Appends characters to the end of the `_bstr_t` object or concatenates two strings.</span></span>

## <a name="syntax"></a><span data-ttu-id="ff21d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ff21d-105">Syntax</span></span>

```
_bstr_t& operator+=( const _bstr_t& s1 );
_bstr_t operator+( const _bstr_t& s1 );
friend _bstr_t operator+( const char* s2, const _bstr_t& s1);
friend _bstr_t operator+( const wchar_t* s3, const _bstr_t& s1);
```

#### <a name="parameters"></a><span data-ttu-id="ff21d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ff21d-106">Parameters</span></span>

<span data-ttu-id="ff21d-107">*S1*</span><span class="sxs-lookup"><span data-stu-id="ff21d-107">*s1*</span></span><br/>
<span data-ttu-id="ff21d-108">A `_bstr_t` nesne.</span><span class="sxs-lookup"><span data-stu-id="ff21d-108">A `_bstr_t` object.</span></span>

<span data-ttu-id="ff21d-109">*S2*</span><span class="sxs-lookup"><span data-stu-id="ff21d-109">*s2*</span></span><br/>
<span data-ttu-id="ff21d-110">Çok baytlı bir dize.</span><span class="sxs-lookup"><span data-stu-id="ff21d-110">A multibyte string.</span></span>

<span data-ttu-id="ff21d-111">*S3*</span><span class="sxs-lookup"><span data-stu-id="ff21d-111">*s3*</span></span><br/>
<span data-ttu-id="ff21d-112">Bir Unicode dize.</span><span class="sxs-lookup"><span data-stu-id="ff21d-112">A Unicode string.</span></span>

## <a name="remarks"></a><span data-ttu-id="ff21d-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ff21d-113">Remarks</span></span>

<span data-ttu-id="ff21d-114">Bu işleçler, dize birleştirme gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="ff21d-114">These operators perform string concatenation:</span></span>

- <span data-ttu-id="ff21d-115">**operator += (***s1***)** kapsüllenmiş karakterler ekler `BSTR` , *s1* sonuna kadar bu nesnenin kapsüllenmiş `BSTR`.</span><span class="sxs-lookup"><span data-stu-id="ff21d-115">**operator+=(**  *s1*  **)** Appends the characters in the encapsulated `BSTR` of *s1* to the end of this object's encapsulated `BSTR`.</span></span>

- <span data-ttu-id="ff21d-116">**operator + (***s1***)** yeni döndürür `_bstr_t` bu nesnenin birleştirerek biçimlendirilmiş `BSTR` değeriyle *s1*.</span><span class="sxs-lookup"><span data-stu-id="ff21d-116">**operator+(**  *s1*  **)** Returns the new `_bstr_t` that is formed by concatenating this object's `BSTR` with that of *s1*.</span></span>

- <span data-ttu-id="ff21d-117">**operator + (***s2***&#124;***s1***)** yeni bir `_bstr_t` birleştirerek biçimlendirilmiş bir çok baytlı bir dize *s2*türüne dönüştürülmüş olarak Unicode ile `BSTR` içinde kapsüllenir *s1*.</span><span class="sxs-lookup"><span data-stu-id="ff21d-117">**operator+(**  *s2*  **&#124;**  *s1*  **)** Returns a new `_bstr_t` that is formed by concatenating a multibyte string *s2*, converted to Unicode, with the `BSTR` encapsulated in *s1*.</span></span>

- <span data-ttu-id="ff21d-118">\**operator + (\*\*\*s3* **,***s1***)** yeni bir `_bstr_t` bir Unicode dize birleştirerek biçimlendirilmiş *s3* ile `BSTR` içinde kapsüllenir *s1*.</span><span class="sxs-lookup"><span data-stu-id="ff21d-118">**operator+(**  *s3* **,**  *s1*  **)** Returns a new `_bstr_t` that is formed by concatenating a Unicode string *s3* with the `BSTR` encapsulated in *s1*.</span></span>

<span data-ttu-id="ff21d-119">**END Microsoft özgü**</span><span class="sxs-lookup"><span data-stu-id="ff21d-119">**END Microsoft Specific**</span></span>

## <a name="see-also"></a><span data-ttu-id="ff21d-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff21d-120">See also</span></span>

[<span data-ttu-id="ff21d-121">_bstr_t Sınıfı</span><span class="sxs-lookup"><span data-stu-id="ff21d-121">_bstr_t Class</span></span>](../cpp/bstr-t-class.md)