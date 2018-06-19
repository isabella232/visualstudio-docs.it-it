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
ms.openlocfilehash: 6663ef73f87ea0fa80eb16a3deef6765265882db
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704132"
---
# <a name="open-project-command"></a>Comando Apri progetto
Apre un progetto esistente.

## <a name="syntax"></a>Sintassi

```cmd
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

```cmd
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>Vedere anche

- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)