---
title: Comando Aggiungi progetto esistente
description: Informazioni sul comando Aggiungi progetto esistente e su come aggiunge un progetto esistente a una soluzione corrente.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 30e2daae72dfd3b5d5a08847ddf87b93d1810a37
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956672"
---
# <a name="add-existing-project-command"></a>Comando Aggiungi progetto esistente
Aggiunge un progetto esistente alla soluzione corrente.

## <a name="syntax"></a>Sintassi

```cmd
File.AddExistingProject filename
```

## <a name="arguments"></a>Argomenti
`filename`\
facoltativo. Percorso completo e nome del progetto comprensivo di estensione da aggiungere alla soluzione.

Se l'argomento `filename` include spazi, deve essere racchiuso tra virgolette.

Se non viene specificato un nome file, il comando aprirà la finestra di dialogo in cui l'utente potrà selezionare un progetto.

## <a name="remarks"></a>Commenti
Il completamento automatico tenta di individuare il percorso e il nome file corretti durante la digitazione.

## <a name="example"></a>Esempio
In questo esempio viene aggiunto il progetto [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] TestProject1 alla soluzione corrente.

```cmd
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"
```

## <a name="see-also"></a>Vedi anche

- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/comando](../../ide/find-command-box.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
