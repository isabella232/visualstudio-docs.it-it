---
title: Apri progetto (comando)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.openproject
- file.opensolution
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5c84a2dcd99ef7cff9b5f37a1c69f235582a7973
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666421"
---
# <a name="open-project-command"></a>Comando Apri progetto

Apre un progetto o una soluzione esistente.

## <a name="syntax"></a>Sintassi

```cmd
File.OpenProject filename
```

## <a name="arguments"></a>argomenti

`filename`

Obbligatorio. Il percorso completo e il nome file del progetto o della soluzione da aprire.

> [!NOTE]
> La sintassi dell'argomento `filename` richiede che i percorsi contenenti spazi usino le virgolette.

## <a name="remarks"></a>Note

Il completamento automatico tenta di individuare il percorso e il nome file corretti durante la digitazione.

Questo comando non è disponibile durante il debug.

## <a name="example"></a>Esempio

L'esempio seguente apre il progetto Visual Basic **Test1**:

```cmd
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>Vedere anche

- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)