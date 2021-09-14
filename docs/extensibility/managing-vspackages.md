---
title: Gestione dei pacchetti VSPackage | Microsoft Docs
description: Informazioni sulla gestione dei pacchetti VSPackage, in modo da sapere quando è possibile usare semplicemente la gestione VSPackage predefinita fornita da Visual Studio e come e quando personalizzarlo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 17afce8065377053494132644b33eb6389d98c74
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709452"
---
# <a name="manage-vspackages"></a>Gestire VSPackage
Nella maggior parte dei casi non è necessario preoccuparsi della gestione dei pacchetti VSPackage, perché i modelli di progetto ed elemento registrano e caricano automaticamente il pacchetto. Tuttavia, in alcune circostanze potrebbe essere necessario acquisire altre informazioni per gestire il pacchetto.

## <a name="use-the-experimental-instance"></a>Usare l'istanza sperimentale
 Per altre informazioni sull'istanza sperimentale, vedere [L'istanza sperimentale](../extensibility/the-experimental-instance.md).

## <a name="register-and-unregister-vspackages"></a>Registrare e annullare la registrazione di pacchetti VSPackage
 Per informazioni su come registrare e annullare la registrazione di pacchetti VSPackage e altri tipi di estensione, vedere Registrare e annullare la registrazione [di pacchetti VSPackage.](../extensibility/registering-and-unregistering-vspackages.md)

## <a name="load-a-vspackage"></a>Caricare un pacchetto VSPackage
 I pacchetti VSPackage possono essere impostati per il caricamento automatico quando è attivato un PARTICOLARE GUID CMDUICONTEXT. Per altre informazioni, vedere [Caricare pacchetti VSPackage.](../extensibility/loading-vspackages.md)

## <a name="use-asyncpackage-to-load-vspackages-in-the-background"></a>Usare AsyncPackage per caricare i pacchetti VSPackage in background
 La classe consente il caricamento dei pacchetti in un thread in background per una migliore velocità di risposta `AsyncPackage` dell'interfaccia utente Visual Studio. Per altre informazioni, [vedere Procedura: Usare AsyncPackage per caricare pacchetti VSPackage in background.](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md)

## <a name="rule-based-ui-context-for-extensions"></a>Contesto dell'interfaccia utente basato su regole per le estensioni
 I contesti dell'interfaccia utente basati su regole consentono agli autori di estensioni di definire le condizioni precise in cui viene attivato un contesto dell'interfaccia utente e vengono caricati i pacchetti VSPackage associati. Per altre informazioni, vedere [Procedura: Usare il contesto dell'interfaccia utente basato](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md)su regole per Visual Studio estensioni .

## <a name="diagnose-extension-performance"></a>Diagnosticare le prestazioni delle estensioni
Le estensioni possono influire sulle prestazioni di avvio e caricamento delle soluzioni. Informazioni su Visual Studio viene calcolato l'impatto dell'estensione e su come può essere analizzata in locale per verificare se un'estensione può essere visualizzata come estensione con impatto sulle prestazioni. Per altre informazioni, vedere [Procedura: Diagnosticare le prestazioni dell'estensione.](how-to-diagnose-extension-performance.md)

## <a name="troubleshoot-vspackages"></a>Risolvere i problemi relativi ai pacchetti VSPackage
 Scoprire le tecniche per la risoluzione dei problemi dei pacchetti VSPackage che non vengono caricati o che riscontrano [errori: Risolvere i problemi relativi ai pacchetti VSPackage](../extensibility/troubleshooting-vspackages.md)

## <a name="see-also"></a>Vedi anche
- [VSPackages](../extensibility/internals/vspackages.md)
