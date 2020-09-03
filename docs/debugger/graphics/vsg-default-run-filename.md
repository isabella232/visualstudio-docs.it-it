---
title: VSG_DEFAULT_RUN_FILENAME | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 835e2cec19e36418091e094abd2ec76bd6403398
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72734836"
---
# <a name="vsg_default_run_filename"></a>VSG_DEFAULT_RUN_FILENAME
Definisce il nome file predefinito del file di log di grafica.

## <a name="syntax"></a>Sintassi

```C++
#define VSG_DEFAULT_FILENAME filename
```

#### <a name="parameters"></a>Parametri
 `filename` Nome file assegnato per impostazione predefinita al file di log di grafica quando le informazioni grafiche vengono acquisite a livello di codice.

## <a name="value"></a>Valore
 Valore letterale stringa che rappresenta il nome del file di log di grafica. Per impostazione predefinita, L"default.vsglog".

```C++
#define VSG_DEFAULT_FILENAME L"default.vsglog"
```

## <a name="remarks"></a>Osservazioni
 Se viene definito il simbolo del preprocessore `DONT_SAVE_VSGLOG_TO_TEMP`, il nome del file è relativo alla directory corrente dell'applicazione acquisita o è un percorso assoluto; in caso contrario, è relativo alla directory dei file temporanei dell'utente e non può essere un percorso assoluto.

 Per modificare il nome del file definito, è necessario ridefinirlo prima `vsgcapture.h` di includere nel programma.

## <a name="example"></a>Esempio
 In questo esempio viene illustrato come modificare il nome file predefinito del file di acquisizione:

```C++
// Redefine the default capture filename before including vsgcapture.h
#define VSG_DEFAULT_FILENAME L"capture.vsglog"

#include <vsgcapture.h>
```

## <a name="see-also"></a>Vedere anche
- [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)