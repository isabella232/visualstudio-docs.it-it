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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6a6b302976495e6067fad14317856cda4ac4625f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709237"
---
# <a name="createexpinstance-utility"></a>Utilità CreateExpInstance
Usare l'utilità **CreateExpInstance** per creare, reimpostare o eliminare un'istanza sperimentale di Visual Studio. È possibile utilizzare l'istanza sperimentale di per eseguire il debug e il test di estensioni di Visual Studio senza modificare il prodotto sottostante.

## <a name="syntax"></a>Sintassi

```
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix
```

## <a name="parameters"></a>Parametri
 **/Create** Crea l'istanza sperimentale.

 **/Reset** Elimina l'istanza sperimentale e ne crea una nuova.

 **/Clean** Elimina l'istanza sperimentale.

 **/VSInstance** Nome della directory che contiene l'istanza di base di Visual Studio da copiare.

 **/Rootsuffix** Suffisso da accodare al nome della directory dell'istanza sperimentale.

## <a name="remarks"></a>Osservazioni
 Quando si utilizza un'estensione di Visual Studio, è possibile premere F5 per aprire l'istanza sperimentale predefinita e installare l'estensione corrente. Se non è disponibile alcuna istanza sperimentale, Visual Studio ne crea una con le impostazioni predefinite.

 Il percorso predefinito dell'istanza sperimentale dipende dal numero di versione di Visual Studio. Per Visual Studio 2015, ad esempio, il percorso è *%LocalAppData%\Microsoft\VisualStudio\14.0Exp \\ *. Tutti i file nel percorso della directory sono considerati parte di tale istanza. Eventuali istanze sperimentali aggiuntive non verranno caricate da Visual Studio, a meno che il nome della directory non venga modificato nel percorso predefinito.

 Visual Studio non accede al registro di sistema quando apre l'istanza sperimentale. Questo comportamento è diverso rispetto alle versioni precedenti di Visual Studio, che hanno usato una versione sperimentale dell'hive del registro di sistema.

 L'utilità **CreateExpInstance** sostituisce l'utilità **VsRegEx** .

 Nell'esempio seguente viene reimpostata l'istanza sperimentale predefinita di Visual Studio:

 **CreateExpInstance.exe/Reset/VSInstance = 14.0/RootSuffix = Exp**

## <a name="see-also"></a>Vedere anche
- [VSPackages](../../extensibility/internals/vspackages.md)
