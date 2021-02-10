---
title: Gestione dei pacchetti VSPackage | Microsoft Docs
description: Informazioni sulla gestione dei pacchetti VSPackage, in modo da sapere quando è possibile usare semplicemente la gestione VSPackage predefinita fornita da Visual Studio e come e quando personalizzarla.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2b0e3b95ee3c715eb21028b6c156b7a62ea82d41
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943218"
---
# <a name="manage-vspackages"></a>Gestire VSPackage
Nella maggior parte dei casi non è necessario preoccuparsi della gestione dei pacchetti VSPackage, dal momento che i modelli di progetto e di elemento si registrano e caricano automaticamente il pacchetto. In alcuni casi, tuttavia, potrebbe essere necessario saperne di più per poter gestire il pacchetto.

## <a name="use-the-experimental-instance"></a>Usare l'istanza sperimentale
 Per ulteriori informazioni sull'istanza sperimentale, vedere [l'istanza sperimentale](../extensibility/the-experimental-instance.md).

## <a name="register-and-unregister-vspackages"></a>Registrare e annullare la registrazione di pacchetti VSPackage
 Per informazioni su come registrare e annullare la registrazione di pacchetti VSPackage e altri tipi di estensione, vedere registrare e annullare la registrazione di [pacchetti VSPackage](../extensibility/registering-and-unregistering-vspackages.md).

## <a name="load-a-vspackage"></a>Caricare un pacchetto VSPackage
 I pacchetti VSPackage possono essere impostati su autoload quando un determinato GUID CMDUICONTEXT è attivato. Per altre informazioni, vedere [caricare i pacchetti VSPackage](../extensibility/loading-vspackages.md).

## <a name="use-asyncpackage-to-load-vspackages-in-the-background"></a>Usare AsyncPackage per caricare i pacchetti VSPackage in background
 La `AsyncPackage` classe Abilita il caricamento di pacchetti in un thread in background per una migliore velocità di risposta dell'interfaccia utente in Visual Studio. Per altre informazioni, vedere [procedura: usare AsyncPackage per caricare VSPackage in background](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).

## <a name="rule-based-ui-context-for-extensions"></a>Contesto dell'interfaccia utente basato su regole per le estensioni
 I contesti dell'interfaccia utente basati su regole consentono agli autori di estensioni di definire le condizioni esatte in cui un contesto dell'interfaccia utente viene attivato e i pacchetti VSPackage associati caricati. Per altre informazioni, vedere [procedura: usare il contesto dell'interfaccia utente basato su regole per le estensioni di Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).

## <a name="diagnose-extension-performance"></a>Diagnosticare le prestazioni delle estensioni
Le estensioni possono compromettere le prestazioni di avvio e di caricamento delle soluzioni. Informazioni sulle modalità di calcolo dell'impatto sulle estensioni di Visual Studio e su come analizzarlo localmente per verificare se un'estensione può essere mostrata come un'estensione di impatto sulle prestazioni. Per altre informazioni, vedere [procedura: diagnosticare le prestazioni delle estensioni](how-to-diagnose-extension-performance.md).

## <a name="troubleshoot-vspackages"></a>Risolvere i problemi relativi ai pacchetti VSPackage
 Informazioni sulle tecniche per la risoluzione dei problemi relativi ai pacchetti VSPackage che non vengono caricati o si verificano errori: [risoluzione dei problemi](../extensibility/troubleshooting-vspackages.md)

## <a name="see-also"></a>Vedi anche
- [VSPackages](../extensibility/internals/vspackages.md)
