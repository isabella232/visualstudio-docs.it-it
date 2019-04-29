---
title: Utilità CreateExpInstance | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2c4f77d0eba4ca974522534c69d554af9d807a9d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62861919"
---
# <a name="createexpinstance-utility"></a>Utilità CreateExpInstance
Usare la **CreateExpInstance** utilità per creare, ripristinare o eliminare un'istanza sperimentale di Visual Studio. È possibile utilizzare l'istanza sperimentale per eseguire il debug e testare le estensioni di Visual Studio senza modificare il prodotto sottostante.

## <a name="syntax"></a>Sintassi

```
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix
```

## <a name="parameters"></a>Parametri
 **/ Creazione** crea l'istanza sperimentale.

 **/ Reimpostazione** Elimina l'istanza sperimentale e quindi ne crea uno nuovo.

 **/ Eliminare** Elimina l'istanza sperimentale.

 **/ VSInstance** il nome della directory che contiene l'istanza di Visual Studio di base da copiare.

 **/ RootSuffix** il suffisso da aggiungere al nome della directory istanza sperimentale.

## <a name="remarks"></a>Note
 Quando si lavora in un'estensione di Visual Studio, è possibile premere F5 per aprire l'istanza sperimentale predefinita e installare l'estensione corrente. Se non è disponibile alcuna istanza sperimentale, Visual Studio crea una con le impostazioni predefinite.

 Il percorso predefinito dell'istanza sperimentale dipende dal numero di versione di Visual Studio. Ad esempio, per Visual Studio 2015, il percorso è *%localappdata%\Microsoft\VisualStudio\14.0Exp\\*. Tutti i file nel percorso della directory sono considerati parte di tale istanza. Eventuali altre istanze sperimentali non verranno caricate da Visual Studio a meno che non viene modificato il nome della directory nel percorso predefinito.

 Visual Studio non accedere Registro di sistema quando si apre l'istanza sperimentale. Questo comportamento differisce dalle versioni precedenti di Visual Studio, che è usata una versione sperimentale dell'hive del Registro di sistema.

 Il **CreateExpInstance** utilità sostituisce il **VsRegEx** utilità.

 L'esempio seguente ripristina l'istanza sperimentale predefinita di Visual Studio:

 **CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp**

## <a name="see-also"></a>Vedere anche
- [Pacchetti VSPackage](../../extensibility/internals/vspackages.md)