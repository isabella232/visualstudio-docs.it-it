---
title: Comando Elenca moduli
description: Informazioni sul comando list modules e sul modo in cui elenca i moduli per il processo corrente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listmodules
helpviewer_keywords:
- Debug.ListModules command
- ListModules command
- list modules command
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4a38a5423568528d267fd92894b8b06b4e5667c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852063"
---
# <a name="list-modules-command"></a>Comando Elenca moduli
Elenca i moduli disponibili per il processo corrente.

## <a name="syntax"></a>Sintassi

```
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]
```

#### <a name="parameters"></a>Parametri
/Address:`yes|no`

facoltativo. Specifica se visualizzare gli indirizzi di memoria dei moduli. Il valore predefinito è `yes`.

/Name:`yes|no`

facoltativo. Specifica se visualizzare i nomi dei moduli. Il valore predefinito è `yes`.

/Order:`yes|no`

facoltativo. Specifica se visualizzare l'ordine dei moduli. Il valore predefinito è `no`.

/Path:`yes|no`

facoltativo. Specifica se visualizzare i percorsi dei moduli. Il valore predefinito è `yes`.

/Process:`yes|no`

facoltativo. Specifica se visualizzare i processi dei moduli. Il valore predefinito è `no`.

/SymbolFile:`yes|no`

facoltativo. Specifica se visualizzare i file dei simboli dei moduli. Il valore predefinito è `no`.

/SymbolStatus:`yes|no`

facoltativo. Specifica se visualizzare lo stato dei simboli dei moduli. Il valore predefinito è `yes`.

/Timestamp:`yes|no`

facoltativo. Specifica se visualizzare il timestamp dei moduli. Il valore predefinito è `no`.

/Version:`yes|no`

facoltativo. Specifica se visualizzare le versioni dei moduli. Il valore predefinito è `no`.

## <a name="example"></a>Esempio
In questo esempio vengono elencati i nomi dei moduli, gli indirizzi e i timestamp per il processo corrente.

```
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no
```

## <a name="see-also"></a>Vedi anche

- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Procedura: utilizzare la finestra Moduli](../../debugger/how-to-use-the-modules-window.md)
