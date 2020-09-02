---
title: Gestione dei pacchetti VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0b56ab490342cfbda9c16408aa0937abd80728c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194384"
---
# <a name="managing-vspackages"></a>Gestione dei pacchetti VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nella maggior parte dei casi non è necessario preoccuparsi della gestione dei pacchetti VSPackage, dal momento che i modelli di progetto e di elemento si registrano e caricano automaticamente il pacchetto. In alcuni casi, tuttavia, potrebbe essere necessario saperne di più per poter gestire il pacchetto.  
  
## <a name="using-the-experimental-instance"></a>Utilizzo dell'istanza sperimentale  
 Per ulteriori informazioni sull'istanza sperimentale, vedere [l'istanza sperimentale](../extensibility/the-experimental-instance.md).  
  
## <a name="registering-and-unregistering-vspackages"></a>Registrazione e annullamento della registrazione di pacchetti VSPackage  
 Per informazioni su come registrare e annullare la registrazione di pacchetti VSPackage e altri tipi di estensione, vedere [registrazione e annullamento della registrazione di pacchetti VSPackage](../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="loading-a-vspackage"></a>Caricamento di un pacchetto VSPackage  
 I pacchetti VSPackage possono essere impostati su autoload quando un determinato GUID CMDUICONTEXT è attivato. Per altre informazioni, vedere [caricamento dei pacchetti VSPackage](../extensibility/loading-vspackages.md).  
  
## <a name="using-asyncpackage-to-load-vspackages-in-the-background"></a>Uso di AsyncPackage per caricare i pacchetti VSPackage in background  
 La classe AsyncPackage consente il caricamento di pacchetti in un thread in background per migliorare la velocità di risposta dell'interfaccia utente in Visual Studio. Per altre informazioni, vedere [procedura: usare AsyncPackage per caricare VSPackage in background](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).  
  
## <a name="rule-based-ui-context-for-extensions"></a>Contesto dell'interfaccia utente basato su regole per le estensioni  
 I contesti dell'interfaccia utente basati su regole consentono agli autori di estensioni di definire le condizioni esatte in cui un contesto dell'interfaccia utente viene attivato e i pacchetti VSPackage associati caricati. Per altre informazioni, vedere [procedura: usare il contesto dell'interfaccia utente basato su regole per le estensioni di Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).  
  
## <a name="troubleshooting-vspackages"></a>Risoluzione dei problemi relativi ai pacchetti VSPackage  
 Informazioni sulle tecniche per la risoluzione dei problemi relativi ai pacchetti VSPackage che non vengono caricati o si verificano errori: [risoluzione dei problemi dei pacchetti VSPackage](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>Vedere anche  
 [VSPackages](../extensibility/internals/vspackages.md)
