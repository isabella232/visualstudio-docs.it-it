---
title: Copia (acquisizione a livello di codice) | Microsoft Docs
description: Usare il metodo Copy della classe VsgDbg per copiare il contenuto del file di log grafico attivo (vsglog) in un nuovo file.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 26a9aff077e3cb7cda6e809546f850fc6a9fc754
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626454"
---
# <a name="copy-programmatic-capture"></a>Copia (acquisizione a livello di codice)
Copiare il contenuto del log di grafica (.vsglog) attivo in un nuovo file.

## <a name="syntax"></a>Sintassi

```C++
void Copy(
  wchar_t const * szNewVSGLog
);
```

#### <a name="parameters"></a>Parametri
 `szNewVSGLog` Nome file del nuovo file di log di grafica.

## <a name="remarks"></a>Commenti
 Per copiare le informazioni grafiche in un nuovo file, è necessario avere già acquisito alcune informazioni grafiche; in caso contrario, non accade nulla.