---
title: Comando Apri progetto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.openproject
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99596442f3aef9e4cb2d890438d29b96cdf4f083
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671914"
---
# <a name="open-project-command"></a>Comando Apri progetto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Apre un progetto esistente.

## <a name="syntax"></a>Sintassi

```
File.OpenProject filename
```

## <a name="arguments"></a>Argomenti
 `filename` Obbligatorio. Percorso completo e nome del file di progetto da aprire.

 La sintassi per l'argomento `filename` richiede che i percorsi contenenti spazi usino le virgolette.

## <a name="remarks"></a>Osservazioni
 Il completamento automatico tenta di individuare il percorso e il nome file corretti durante la digitazione.

 Questo comando non è disponibile durante il debug.

## <a name="example"></a>Esempio
 In questo esempio viene aperto il progetto [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] Test1.

```
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>Vedere anche
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md) [finestra](../../ide/reference/command-window.md) di comando [Trova/comando riquadro](../../ide/find-command-box.md) di [Visual Studio alias di comando](../../ide/reference/visual-studio-command-aliases.md)
