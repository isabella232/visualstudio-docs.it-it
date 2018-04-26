---
title: Comando Apri progetto
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.openproject
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09241e72119a0a0973995b16152941bbe5272c3f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="open-project-command"></a>Comando Apri progetto
Apre un progetto esistente.

## <a name="syntax"></a>Sintassi

```
File.OpenProject filename
```

## <a name="arguments"></a>Argomenti
 `filename`

 Obbligatorio. Percorso completo e nome del file di progetto da aprire.

 La sintassi per l'argomento `filename` richiede che i percorsi contenenti spazi usino le virgolette.

## <a name="remarks"></a>Note
 Il completamento automatico tenta di individuare il percorso e il nome file corretti durante la digitazione.

 Questo comando non è disponibile durante il debug.

## <a name="example"></a>Esempio
 In questo esempio viene aperto il progetto [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Test1.

```
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>Vedere anche

- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)