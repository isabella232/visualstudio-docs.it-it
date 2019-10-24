---
title: Comando Aggiungi progetto esistente
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05d57024c52e0a35d7e387f5ba3cccf0697fe44a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748843"
---
# <a name="add-existing-project-command"></a>Comando Aggiungi progetto esistente
Aggiunge un progetto esistente alla soluzione corrente.

## <a name="syntax"></a>Sintassi

```cmd
File.AddExistingProject filename
```

## <a name="arguments"></a>argomenti
`filename`\
Parametro facoltativo. Percorso completo e nome del progetto comprensivo di estensione da aggiungere alla soluzione.

Se l'argomento `filename` include spazi, deve essere racchiuso tra virgolette.

Se non viene specificato un nome file, il comando aprirà la finestra di dialogo in cui l'utente potrà selezionare un progetto.

## <a name="remarks"></a>Note
Il completamento automatico tenta di individuare il percorso e il nome file corretti durante la digitazione.

## <a name="example"></a>Esempio
In questo esempio viene aggiunto il progetto [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] TestProject1 alla soluzione corrente.

```cmd
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"
```

## <a name="see-also"></a>Vedere anche

- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)