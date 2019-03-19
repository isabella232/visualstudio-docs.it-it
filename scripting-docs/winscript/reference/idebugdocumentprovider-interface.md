---
title: Interfaccia IDebugDocumentProvider | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentProvider interface
ms.assetid: 36510acf-1ef9-479c-a430-d3f09502f82c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5632134c86b5aa0e3cb769a68d2d4cfd944ff35c
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157210"
---
# <a name="idebugdocumentprovider-interface"></a>Interfaccia IDebugDocumentProvider
Specifica i mezzi per creare un'istanza di un documento su richiesta.  
  
## <a name="remarks"></a>Note  
 In questo modo indiretto per creare un'istanza di un documento:  
  
- Consente il documento da caricare quando è necessaria.  
  
- Consente all'oggetto documento devono essere contenuti all'interno del debugger dell'IDE.  
  
- Consente a diversi modi accedere all'oggetto documento stesso.  
  
  Questo efficace separa il documento dal relativo provider e consente al provider per altre informazioni sul contesto di runtime, eseguire.  
  
  Oltre ai metodi ereditati da `IDebugDocumentInfo`, il `IDebugDocumentProvider` interfaccia espone i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugDocumentProvider::GetDocument](../../winscript/reference/idebugdocumentprovider-getdocument.md)|Fa sì che il documento venga creata un'istanza se non esiste già.|