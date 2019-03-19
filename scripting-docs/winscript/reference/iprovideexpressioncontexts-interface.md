---
title: IProvideExpressionContexts Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IProvideExpressionContexts interface
ms.assetid: e4c70f2c-7d86-4fdc-a1cb-f5a0bb8ed037
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b40825884b3c63af6be6d8bc852a5da4805f8975
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152051"
---
# <a name="iprovideexpressioncontexts-interface"></a>Interfaccia IProvideExpressionContexts
Consente di enumerare i contesti di espressione noti a un determinato componente. Motori di script in genere implementano questa interfaccia.  
  
 Il gestore di debug di processi Usa questa interfaccia per trovare tutti i contesti di espressione globale associati a un determinato thread.  
  
> [!NOTE]
>  Questa interfaccia viene chiamata dall'interno del thread di interesse. Spetta all'implementatore di identificare il thread corrente e restituisce un enumeratore appropriato.  
  
## <a name="methods"></a>Metodi  
 Oltre ai metodi ereditati da `IUnknown`, il `IProvideExpressionContexts` interfaccia espone i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IProvideExpressionContexts::EnumExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-enumexpressioncontexts.md)|Restituisce un enumeratore dei contesti di espressione noti da questo componente.|