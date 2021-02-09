---
title: Apri progetto (comando)
description: Informazioni sul comando Apri progetto e su come viene aperto un progetto o una soluzione esistente.
ms.custom: SEO-VS-2020
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
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4298c840094f7f1f75e58be1b25213cdf66a6674
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881970"
---
# <a name="open-project-command"></a>Comando Apri progetto

Apre un progetto o una soluzione esistente.

## <a name="syntax"></a>Sintassi

```cmd
File.OpenProject filename
```

## <a name="arguments"></a>Argomenti

`filename`

Obbligatorio. Il percorso completo e il nome file del progetto o della soluzione da aprire.

> [!NOTE]
> La sintassi dell'argomento `filename` richiede che i percorsi contenenti spazi usino le virgolette.

## <a name="remarks"></a>Commenti

Il completamento automatico tenta di individuare il percorso e il nome file corretti durante la digitazione.

Questo comando non è disponibile durante il debug.

## <a name="example"></a>Esempio

L'esempio seguente apre il progetto Visual Basic **Test1**:

```cmd
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>Vedi anche

- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/comando](../../ide/find-command-box.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
