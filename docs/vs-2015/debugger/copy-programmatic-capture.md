---
title: Copia (acquisizione a livello di codice) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fa79ffc2081ba92b905838658fe6aa758a675192
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58964515"
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
