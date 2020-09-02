---
title: -Edit (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Edit Devenv switch
- Devenv, /Edit switch
- /Edit Devenv switch
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d180d5a5d723d8085537f2993aac022d74df2c08
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75595696"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)

Apre il file specificato in un'istanza esistente di Visual Studio.

## <a name="syntax"></a>Sintassi

```shell
devenv /Edit [File1[ FileN]...]
```

## <a name="arguments"></a>Argomenti

- *File1*

  facoltativo. File da aprire in un'istanza esistente di Visual Studio. Se non esiste alcuna istanza di Visual Studio, viene creata una nuova istanza con un layout di finestra semplificato e lo strumento apre *File1* nella nuova istanza.

- *FileN*

  facoltativo. Uno o più file aggiuntivi da aprire nell'istanza esistente di Visual Studio.

## <a name="remarks"></a>Osservazioni

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
