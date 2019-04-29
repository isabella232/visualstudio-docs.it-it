---
title: Interfaccia ISetNextStatement | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: b570c2e0-a173-4f14-97d8-f39465753115
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de300a7af8492e6431f6b8513cde84a15895ad96
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786308"
---
# <a name="isetnextstatement-interface"></a>Interfaccia ISetNextStatement
Questa interfaccia viene implementata da un interprete per consentire il gestore di eseguire il Debug di processi aggiornare l'istruzione corrente. Viene implementato da un oggetto stack frame e PDM ottiene questa interfaccia tramite QueryInterface.  
  
 interfaccia fornisce metodi che sono utili per l'impostazione del punto di esecuzione, che determina l'istruzione successiva da eseguire.  
  
 Oltre ai metodi ereditati da `IUnknown`, il `ISetNextStatement` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[ISetNextStatement::CanSetNextStatement](../../winscript/reference/isetnextstatement-cansetnextstatement.md)|Determina se il punto di esecuzione è possibile impostare nel percorso specificato.|  
|[ISetNextStatement::SetNextStatement](../../winscript/reference/isetnextstatement-setnextstatement.md)|Imposta il punto di esecuzione nella posizione specificata.|