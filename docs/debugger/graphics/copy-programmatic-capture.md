---
title: Copia (acquisizione a livello di codice) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3a888605cfae6b5430782defd198f83988c31870
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56719080"
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

## <a name="remarks"></a>Osservazioni
 Per copiare le informazioni grafiche in un nuovo file, è necessario avere già acquisito alcune informazioni grafiche; in caso contrario, non accade nulla.