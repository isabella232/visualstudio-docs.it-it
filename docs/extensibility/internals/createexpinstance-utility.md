---
title: Utilità CreateExpInstance | Microsoft Docs
description: Informazioni sull'utilità CreateExpInstance che consente di creare, reimpostare o eliminare un'istanza sperimentale di Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 91046edab4693adee21b13616ab8d2f2c1259f11053829bdad23ebcb797bc9ca
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121448182"
---
# <a name="createexpinstance-utility"></a>Utilità CreateExpInstance
Usare **l'utilità CreateExpInstance** per creare, reimpostare o eliminare un'istanza sperimentale di Visual Studio. È possibile usare l'istanza sperimentale per eseguire il debug e il test Visual Studio estensioni senza modificare il prodotto sottostante.

## <a name="syntax"></a>Sintassi

```
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix
```

## <a name="parameters"></a>Parametri
 **/Create** Crea l'istanza sperimentale.

 **/Reset** Elimina l'istanza sperimentale e quindi ne crea una nuova.

 **/Clean** Elimina l'istanza sperimentale.

 **/VSInstance** Nome della directory che contiene l'istanza Visual Studio base da copiare.

 **/RootSuffix** Suffisso da aggiungere al nome della directory dell'istanza sperimentale.

## <a name="remarks"></a>Commenti
 Quando si lavora a un'estensione Visual Studio, è possibile premere F5 per aprire l'istanza sperimentale predefinita e installare l'estensione corrente. Se non è disponibile alcuna istanza sperimentale, Visual Studio ne crea una con le impostazioni predefinite.

 Il percorso predefinito dell'istanza sperimentale dipende dal numero Visual Studio versione. Ad esempio, per Visual Studio 2015, il percorso è *%localappdata%\Microsoft\VisualStudio\14.0Exp \\*. Tutti i file nel percorso della directory sono considerati parte di tale istanza. Eventuali istanze sperimentali aggiuntive non verranno caricate da Visual Studio a meno che il nome della directory non venga modificato nel percorso predefinito.

 Visual Studio non accede al Registro di sistema quando apre l'istanza sperimentale. Questo comportamento è diverso dalle versioni precedenti di Visual Studio, che usava una versione sperimentale dell'hive del Registro di sistema.

 **L'utilità CreateExpInstance** sostituisce **l'utilità VsRegEx.**

 L'esempio seguente reimposta l'istanza sperimentale predefinita di Visual Studio:

 **CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp**

## <a name="see-also"></a>Vedi anche
- [VSPackages](../../extensibility/internals/vspackages.md)
