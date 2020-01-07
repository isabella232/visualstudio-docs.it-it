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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 008802546d87bd44137c6d13ee2aef802877e308
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595878"
---
# <a name="add-existing-project-command"></a>Comando Aggiungi progetto esistente
Aggiunge un progetto esistente alla soluzione corrente.

## <a name="syntax"></a>Sintassi

```cmd
File.AddExistingProject filename
```

## <a name="arguments"></a>Argomenti
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
- [Command Window](../../ide/reference/command-window.md) (Finestra di comando)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
