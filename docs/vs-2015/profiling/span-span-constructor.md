---
title: Costruttore span::span | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::span::span
helpviewer_keywords:
- Concurrency::diagnostic::span constructor
ms.assetid: 8b5578aa-5e5c-4ac7-87c7-ce87c4246e2c
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bd371fac572c347ae2b5299f085f5e063306fc1b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54783043"
---
# <a name="spanspan-constructor"></a>Costruttore span::span
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Inizializza una nuova istanza della classe `span`.  
  
## <a name="syntax"></a>Sintassi  
  
```  
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
 `_Series`  
 Contesto della serie di marcatori valido.  
  
 `_Format`  
 Stringa di formato composta che contiene testo combinato con zero o più elementi di formato, che corrispondono agli oggetti nell'elenco degli argomenti.  
  
 `_Importance`  
 Livello di importanza.  
  
 `_Category`  
 Categoria.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** cvmarkersobj.h  
  
 **Spazio dei nomi:** Concurrency::diagnostic
 
 ## <a name="see-also"></a>Vedere anche
 [Classe span](../profiling/span-class.md)
