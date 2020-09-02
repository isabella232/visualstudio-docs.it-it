---
title: Registrazione di pacchetti VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 053157b0ce1cb4250d8c666725431515c75b5fa2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157381"
---
# <a name="registering-vspackages"></a>Registrazione di pacchetti VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] si basa sui file. pkgdef per descrivere e individuare un pacchetto VSPackage. Un file. pkgdef contiene tutte le informazioni di registrazione che altrimenti verrebbero aggiunte al registro di sistema. I pacchetti VSPackage gestiti vengono registrati aggiungendo attributi al codice sorgente e quindi eseguendo l' [utilità CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) nell'assembly risultante per generare un file con estensione pkgdef.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Definizione del percorso di file VSPackage nella shell di Visual Studio](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Descrive il percorso di caricamento per i pacchetti VSPackage.  
  
 [Registrazione e annullamento della registrazione di pacchetti VSPackage](../../extensibility/registering-and-unregistering-vspackages.md)  
 Viene illustrato come registrare un pacchetto VSPackage.  
  
 [Uso di un attributo di registrazione personalizzato per registrare un'estensione](../../misc/using-a-custom-registration-attribute-to-register-an-extension.md)  
 Viene descritto come creare un manifesto di registrazione che può essere usato per distribuire un pacchetto VSPackage gestito.
