---
title: Utilità CreateExpInstance | Microsoft Docs
description: Informazioni sull'utilità CreateExpInstance che consente di creare, reimpostare o eliminare un'istanza sperimentale di Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.workload:
- vssdk
ms.openlocfilehash: d0010c4a98d0ea50ec7feb2f7a379f3c84bc3d53
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056987"
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

## <a name="remarks"></a>Commenti
 Quando si utilizza un'estensione di Visual Studio, è possibile premere F5 per aprire l'istanza sperimentale predefinita e installare l'estensione corrente. Se non è disponibile alcuna istanza sperimentale, Visual Studio ne crea una con le impostazioni predefinite.

 Il percorso predefinito dell'istanza sperimentale dipende dal numero di versione di Visual Studio. Per Visual Studio 2015, ad esempio, il percorso è *%LocalAppData%\Microsoft\VisualStudio\14.0Exp \\*. Tutti i file nel percorso della directory sono considerati parte di tale istanza. Eventuali istanze sperimentali aggiuntive non verranno caricate da Visual Studio, a meno che il nome della directory non venga modificato nel percorso predefinito.

 Visual Studio non accede al registro di sistema quando apre l'istanza sperimentale. Questo comportamento è diverso rispetto alle versioni precedenti di Visual Studio, che hanno usato una versione sperimentale dell'hive del registro di sistema.

 L'utilità **CreateExpInstance** sostituisce l'utilità **VsRegEx** .

 Nell'esempio seguente viene reimpostata l'istanza sperimentale predefinita di Visual Studio:

 **CreateExpInstance.exe/Reset/VSInstance = 14.0/RootSuffix = Exp**

## <a name="see-also"></a>Vedi anche
- [VSPackages](../../extensibility/internals/vspackages.md)
