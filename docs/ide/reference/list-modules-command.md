---
title: Comando Elenca moduli
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e083a0e1baeefc6807dccb2199cd0e5a9bd883d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595501"
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

Facoltativa. Specifica se visualizzare gli indirizzi di memoria dei moduli. Il valore predefinito è `yes`.

/Name:`yes|no`

Facoltativa. Specifica se visualizzare i nomi dei moduli. Il valore predefinito è `yes`.

/Order:`yes|no`

Facoltativa. Specifica se visualizzare l'ordine dei moduli. Il valore predefinito è `no`.

/Path:`yes|no`

Facoltativa. Specifica se visualizzare i percorsi dei moduli. Il valore predefinito è `yes`.

/Process:`yes|no`

Facoltativa. Specifica se visualizzare i processi dei moduli. Il valore predefinito è `no`.

/SymbolFile:`yes|no`

Facoltativa. Specifica se visualizzare i file dei simboli dei moduli. Il valore predefinito è `no`.

/SymbolStatus:`yes|no`

Facoltativa. Specifica se visualizzare lo stato dei simboli dei moduli. Il valore predefinito è `yes`.

/Timestamp:`yes|no`

Facoltativa. Specifica se visualizzare il timestamp dei moduli. Il valore predefinito è `no`.

/Version:`yes|no`

Facoltativa. Specifica se visualizzare le versioni dei moduli. Il valore predefinito è `no`.

## <a name="example"></a>Esempio
In questo esempio vengono elencati i nomi dei moduli, gli indirizzi e i timestamp per il processo corrente.

```
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no
```

## <a name="see-also"></a>Vedere anche

- [Visual Studio Commands](../../ide/reference/visual-studio-commands.md) (Comandi di Visual Studio)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Procedura: utilizzare la finestra Moduli](../../debugger/how-to-use-the-modules-window.md)
