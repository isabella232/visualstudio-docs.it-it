---
title: -Edit (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Edit Devenv switch
- Devenv, /Edit switch
- /Edit Devenv switch
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 37d49dd7d191ad470639debc50fbed23d5066233
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654479"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)

Apre il file specificato in un'istanza esistente di Visual Studio.

## <a name="syntax"></a>Sintassi

```shell
devenv /Edit [File1[ FileN]...]
```

## <a name="arguments"></a>argomenti

- *File1*

  Parametro facoltativo. File da aprire in un'istanza esistente di Visual Studio. Se non esiste alcuna istanza di Visual Studio, viene creata una nuova istanza con un layout di finestra semplificato e lo strumento apre *File1* nella nuova istanza.

- *FileN*

  Parametro facoltativo. Uno o più file aggiuntivi da aprire nell'istanza esistente di Visual Studio.

## <a name="remarks"></a>Note

Quando non viene specificato un file, un'istanza esistente di Visual Studio riceve lo stato attivo. Se non viene specificato alcun file e non esiste un'istanza di Visual Studio, lo strumento crea un'istanza con un layout di finestra semplificato.

Se l'istanza esistente di Visual Studio è in uno stato modale, il file viene aperto nell'istanza esistente quando Visual Studio esce dallo stato modale. Ad esempio, questa situazione può verificarsi quando la [finestra di dialogo Opzioni](../../ide/reference/options-dialog-box-visual-studio.md) è aperta.

Se è aperta più di un'istanza di Visual Studio, il file viene aperto nell'istanza aperta più di recente.

## <a name="example"></a>Esempio

Il primo esempio apre il file `MyFile.cs` in un'istanza esistente di Visual Studio. Se non esiste un'istanza di Visual Studio, lo strumento apre il file in una nuova istanza. Il secondo esempio è simile, ad eccezione del fatto che apre tre file anziché uno solo.

```shell
devenv /edit MyFile.cs

devenv /edit MyFile1.cs MyFile2.cs MyFile3.cs
```

## <a name="see-also"></a>Vedere anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
