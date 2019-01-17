---
title: Interfaccia IDebugDocumentProvider | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: d775deb153205d0e9a452775272285c67e74a210
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345214"
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