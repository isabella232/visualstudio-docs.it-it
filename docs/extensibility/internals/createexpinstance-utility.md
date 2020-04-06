---
title: 'Utilità CreateExpInstance : Documenti Microsoft'
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709237"
---
# <a name="createexpinstance-utility"></a>Utilità CreateExpInstance
Utilizzare l'utilità **CreateExpInstance** per creare, reimpostare o eliminare un'istanza sperimentale di Visual Studio. È possibile utilizzare l'istanza sperimentale per eseguire il debug e testare le estensioni di Visual Studio senza modificare il prodotto sottostante.

## <a name="syntax"></a>Sintassi

```
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix
```

## <a name="parameters"></a>Parametri
 **/Create (Crea)** Crea l'istanza sperimentale.

 **/Reset (Ripristina)** Elimina l'istanza sperimentale e ne crea una nuova.

 **/Pulisci** Elimina l'istanza sperimentale.

 **/VSIstanza** Nome della directory che contiene l'istanza di Visual Studio di base da copiare.

 **/RootSuffix (Opzione /RootSuffix)** Suffisso da aggiungere al nome della directory dell'istanza sperimentale.

## <a name="remarks"></a>Osservazioni
 Quando si lavora su un'estensione di Visual Studio, è possibile premere F5 per aprire l'istanza sperimentale predefinita e installare l'estensione corrente. Se non è disponibile alcuna istanza sperimentale, Visual Studio ne crea una con le impostazioni predefinite.

 Il percorso predefinito dell'istanza sperimentale dipende dal numero di versione di Visual Studio. Ad esempio, per Visual Studio 2015, il percorso è *%localappdata%\\* Tutti i file nel percorso della directory sono considerati parte di tale istanza. Eventuali istanze sperimentali aggiuntive non verranno caricate da Visual Studio a meno che il nome della directory non venga modificato nel percorso predefinito.

 Visual Studio non accede al Registro di sistema quando apre l'istanza sperimentale. Questo comportamento è diverso dalle versioni precedenti di Visual Studio, che utilizzava una versione sperimentale dell'hive del Registro di sistema.

 L'utilità **CreateExpInstance** sostituisce l'utilità **VsRegEx.**

 The following example resets the default experimental instance of Visual Studio:

 **CreateExpInstance.exe /Reset /VSInstance**

## <a name="see-also"></a>Vedere anche
- [Pacchetti VSPackage](../../extensibility/internals/vspackages.md)
