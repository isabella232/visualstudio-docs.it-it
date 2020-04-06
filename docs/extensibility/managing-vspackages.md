---
title: Gestione di VSPackage Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60745d07679ae53b85d169473ed37ab314b67624
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702644"
---
# <a name="manage-vspackages"></a>Gestire VSPackage
Nella maggior parte dei casi non è necessario preoccuparsi di gestione VSPackage, poiché i modelli di progetto e di elemento registrare e caricare automaticamente il pacchetto. Tuttavia, in alcune circostanze potrebbe essere necessario imparare un po 'di più per gestire il pacchetto.

## <a name="use-the-experimental-instance"></a>Utilizzare l'istanza sperimentale
 Per ulteriori informazioni sull'istanza sperimentale, vedere [L'istanza sperimentale](../extensibility/the-experimental-instance.md).

## <a name="register-and-unregister-vspackages"></a>Registrare e annullare la registrazione di VSPackageRegister and unregister VSPackages
 Per informazioni su come registrare e annullare la registrazione di VSPackage e altri tipi di estensione, vedere [Registrare e annullare la registrazione di VSPackage](../extensibility/registering-and-unregistering-vspackages.md).

## <a name="load-a-vspackage"></a>Caricare un pacchetto VSPackageLoad a VSPackage
 VSPackage possono essere impostati per il caricamento automatico quando un particolare GUID CMDUICONTEXT è attivato. Per ulteriori informazioni, vedere [Caricare VSPackage](../extensibility/loading-vspackages.md).

## <a name="use-asyncpackage-to-load-vspackages-in-the-background"></a>Usare AsyncPackage per caricare VSPackage in backgroundUse AsyncPackage to load VSPackages in the background
 La `AsyncPackage` classe abilita il caricamento del pacchetto in un thread in background per una migliore velocità di risposta dell'interfaccia utente in Visual Studio.The class enables package loading on a background thread for better UI responsiveness in Visual Studio. Per ulteriori informazioni, vedere [Procedura: utilizzare AsyncPackage per caricare VSPackage in background.](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md)

## <a name="rule-based-ui-context-for-extensions"></a>Contesto dell'interfaccia utente basata su regole per le estensioniRule-based UI Context for extensions
 Contesti dell'interfaccia utente basati su regole consente agli autori di estensione definire le condizioni precise in cui un contesto dell'interfaccia utente viene attivato e VSPackage associati caricati. Per ulteriori informazioni, vedere Procedura: utilizzare il [contesto dell'interfaccia utente basato su regole per le estensioni](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md)di Visual Studio .

## <a name="diagnose-extension-performance"></a>Diagnosticare le prestazioni delle estensioni
Le estensioni possono influire sulle prestazioni di avvio e caricamento della soluzione. Informazioni su come viene calcolato l'impatto dell'estensione di Visual Studio e su come è possibile analizzarlo localmente per verificare se un'estensione può essere visualizzata come estensione che influisce sulle prestazioni. Per ulteriori informazioni, vedere [Procedura: diagnosticare le prestazioni delle estensioni](how-to-diagnose-extension-performance.md).

## <a name="troubleshoot-vspackages"></a>Risolvere i problemi relativi ai pacchetti VSPackageTroubleshoot VS
 Scopri le tecniche per la risoluzione dei problemi VSPackage che non caricano o si verificano errori: [Risolvere i problemi VSPackage](../extensibility/troubleshooting-vspackages.md)

## <a name="see-also"></a>Vedere anche
- [Pacchetti VSPackage](../extensibility/internals/vspackages.md)
