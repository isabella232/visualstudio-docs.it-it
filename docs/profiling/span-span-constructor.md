---
title: Costruttore span::span | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::span::span
helpviewer_keywords:
- Concurrency::diagnostic::span constructor
ms.assetid: 8b5578aa-5e5c-4ac7-87c7-ce87c4246e2c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f761e87c1658c11bfdfd93a4f4e22299d88575a8
ms.sourcegitcommit: cea6187005f8a0cdf44e866a1534a4cf5356208c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/27/2019
ms.locfileid: "56953301"
---
# <a name="spanspan-constructor"></a>Costruttore span::span

Inizializza una nuova istanza della classe `span`.

## <a name="syntax"></a>Sintassi

```cpp
span(
   const marker_series& _Series,
   _In_ LPCTSTR _Format,
   ...
);
span(
   const marker_series& _Series,
   marker_importance _Importance,
   _In_ LPCTSTR _Format,
   ...
);
span(
   const marker_series& _Series,
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
span(
   const marker_series& _Series,
   marker_importance _Importance,
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
```

#### <a name="parameters"></a>Parametri

`_Series` Contesto della serie di marcatori valido.

`_Format` Stringa di formato composito che contiene testo combinato con zero o più elementi di formato, che corrispondono agli oggetti nell'elenco degli argomenti.

`_Importance` Livello di importanza.

`_Category` Categoria.

## <a name="requirements"></a>Requisiti

**Intestazione:** *cvmarkersobj.h*

**Spazio dei nomi:** Concurrency::diagnostic

## <a name="see-also"></a>Vedere anche

- [Classe span](../profiling/span-class.md)