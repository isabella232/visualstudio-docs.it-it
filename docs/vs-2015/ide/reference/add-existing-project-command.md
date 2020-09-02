---
title: Comando Aggiungi progetto esistente | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 73d8e54938659920227b3614046b8a8f933023ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670219"
---
# <a name="add-existing-project-command"></a>Comando Aggiungi progetto esistente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aggiunge un progetto esistente alla soluzione corrente.

## <a name="syntax"></a>Sintassi

```
File.AddExistingProject filename
```

## <a name="arguments"></a>Argomenti
 `filename` Facoltativo. Percorso completo e nome del progetto comprensivo di estensione da aggiungere alla soluzione.

 Se l'argomento `filename` include spazi, deve essere racchiuso tra virgolette.

 Se non viene specificato un nome file, il comando aprirà la finestra di dialogo in cui l'utente potrà selezionare un progetto.

## <a name="remarks"></a>Osservazioni
 Il completamento automatico tenta di individuare il percorso e il nome file corretti durante la digitazione.

## <a name="example"></a>Esempio
 In questo esempio viene aggiunto il progetto [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] TestProject1 alla soluzione corrente.

```
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"
```

## <a name="see-also"></a>Vedere anche
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md) [finestra](../../ide/reference/command-window.md) di comando [Trova/comando riquadro](../../ide/find-command-box.md) di [Visual Studio alias di comando](../../ide/reference/visual-studio-command-aliases.md)
