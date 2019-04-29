---
title: Interfaccia IProcessDebugManager | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IProcessDebugManager interface
ms.assetid: b6ecb2bd-a4d1-4857-9232-036c154d0cb1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d68c044cdc3d523841cc56814b8ca34bcd8aa037
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62944793"
---
# <a name="iprocessdebugmanager-interface"></a>Interfaccia IProcessDebugManager
Interfaccia principale con la gestione del debug dei processi. Questa interfaccia può creare, aggiungere o rimuovere un'applicazione virtuale da un processo. È possibile enumerare gli stack frame e thread dell'applicazione.  
  
 Oltre ai metodi ereditati da `IUnknown`, il `IProcessDebugManager` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IProcessDebugManager::CreateApplication](../../winscript/reference/iprocessdebugmanager-createapplication.md)|Crea un nuovo oggetto di applicazione di debug per questa applicazione.|  
|[IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)|Restituisce un oggetto di applicazione predefinito per il processo corrente.|  
|[IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)|Aggiunge un'applicazione elenco di gestione debug del computer delle applicazioni in esecuzione.|  
|[IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)|Rimuove l'esecuzione di un'applicazione elenco di applicazioni.|  
|[IProcessDebugManager::CreateDebugDocumentHelper](../../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md)|Crea un nuovo helper di documenti di debug per questa applicazione.|