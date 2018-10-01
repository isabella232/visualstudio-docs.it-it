---
title: Copia (acquisizione a livello di codice) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 171dd04a4f2c933272a7addc787554f611b1449f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529106"
---
# <a name="copy-programmatic-capture"></a>Copia (acquisizione a livello di codice)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [copia (acquisizione a livello di codice)](https://docs.microsoft.com/visualstudio/debugger/graphics/copy-programmatic-capture).  
  
Copiare il contenuto del log di grafica (.vsglog) attivo in un nuovo file.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
void Copy(  
  wchar_t const * szNewVSGLog  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `szNewVSGLog`  
 Nome file del nuovo file di log di grafica.  
  
## <a name="remarks"></a>Note  
 Per copiare le informazioni grafiche in un nuovo file, è necessario avere già acquisito alcune informazioni grafiche; in caso contrario, non accade nulla.



