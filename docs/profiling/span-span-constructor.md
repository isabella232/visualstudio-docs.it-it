---
description: Inizializza una nuova istanza della classe Span.
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fdffdc59b31f5f04817536769d9a712484e6cdd7
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223862"
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

## <a name="see-also"></a>Vedi anche

- [classe Span](../profiling/span-class.md)
