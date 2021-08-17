---
title: Gestione dei pacchetti VSPackage | Microsoft Docs
description: Informazioni sulla gestione dei pacchetti VSPackage, in modo da sapere quando è possibile usare semplicemente la gestione vspackage predefinita fornita da Visual Studio e come e quando personalizzarla.
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
ms.openlocfilehash: af813e57420cfcb5c583af18790f5399cb54be47f1f1dc959ec1d6d451951711
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121401063"
---
# <a name="manage-vspackages"></a>Gestire VSPackage
Nella maggior parte dei casi non è necessario preoccuparsi della gestione dei pacchetti VSPackage, poiché i modelli di progetto e di elemento registrano e caricano automaticamente il pacchetto. Tuttavia, in alcuni casi potrebbe essere necessario imparare un po' di più per gestire il pacchetto.

## <a name="use-the-experimental-instance"></a>Usare l'istanza sperimentale
 Per altre informazioni sull'istanza sperimentale, vedere [Istanza sperimentale](../extensibility/the-experimental-instance.md).

## <a name="register-and-unregister-vspackages"></a>Registrare e annullare la registrazione di VSPackage
 Per informazioni su come registrare e annullare la registrazione di VSPackage e altri tipi di estensione, vedere Registrare e annullare la registrazione [di VSPackage.](../extensibility/registering-and-unregistering-vspackages.md)

## <a name="load-a-vspackage"></a>Caricare un VSPackage
 I pacchetti VSPackage possono essere impostati per il caricamento automatico quando è attivato un GUID CMDUICONTEXT specifico. Per altre informazioni, vedere [Caricare VSPackage.](../extensibility/loading-vspackages.md)

## <a name="use-asyncpackage-to-load-vspackages-in-the-background"></a>Usare AsyncPackage per caricare VSPackage in background
 La classe abilita il caricamento dei pacchetti in un thread in background per migliorare la velocità di risposta `AsyncPackage` dell'interfaccia utente Visual Studio. Per altre informazioni, vedere [Procedura: Usare AsyncPackage per caricare VSPackage in background.](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md)

## <a name="rule-based-ui-context-for-extensions"></a>Contesto dell'interfaccia utente basato su regole per le estensioni
 Contesti dell'interfaccia utente basati su regole consente agli autori di estensioni di definire le condizioni precise in cui viene attivato un contesto dell'interfaccia utente e vengono caricati i pacchetti VSPackage associati. Per altre informazioni, vedere [Procedura: Usare il contesto dell'interfaccia](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md)utente basato su regole per Visual Studio estensioni .

## <a name="diagnose-extension-performance"></a>Diagnosticare le prestazioni delle estensioni
Le estensioni possono influire sulle prestazioni di avvio e caricamento della soluzione. Informazioni su Visual Studio'impatto sull'estensione e su come può essere analizzata in locale per verificare se un'estensione può essere visualizzata come estensione che influisce sulle prestazioni. Per altre informazioni, vedere [Procedura: Diagnosticare le prestazioni dell'estensione.](how-to-diagnose-extension-performance.md)

## <a name="troubleshoot-vspackages"></a>Risolvere i problemi relativi ai pacchetti VSPackage
 Informazioni sulle tecniche per la risoluzione dei problemi relativi ai pacchetti VSPackage che non vengono caricati o che si verificano errori: [Risolvere i problemi relativi ai pacchetti VSPackage](../extensibility/troubleshooting-vspackages.md)

## <a name="see-also"></a>Vedi anche
- [VSPackages](../extensibility/internals/vspackages.md)
