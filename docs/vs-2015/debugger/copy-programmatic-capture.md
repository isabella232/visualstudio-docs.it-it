---
title: Copia (acquisizione a livello di codice) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: 7ec5c95a2419e465f93f7d11045672de2f1b0174
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49293189"
---
# <a name="copy-programmatic-capture"></a>Copia (acquisizione a livello di codice)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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



