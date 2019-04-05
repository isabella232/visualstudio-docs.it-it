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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58965242"
---
# <a name="registering-vspackages"></a>Registrazione di pacchetti VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] si basa sui file con estensione pkgdef per descrivere e individuare un pacchetto VSPackage. Un file con estensione pkgdef contiene tutte le informazioni di registrazione che altrimenti verrebbero aggiunti al Registro di sistema. I VSPackage gestiti sono registrati aggiungendo attributi al codice sorgente e quindi eseguendo il [utilità CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) sull'assembly risultante per generare un file. pkgdef.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Definizione del percorso di file VSPackage nella shell di Visual Studio](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Descrive il percorso di caricamento per i pacchetti VSPackage.  
  
 [Registrazione e annullamento della registrazione di pacchetti VSPackage](../../extensibility/registering-and-unregistering-vspackages.md)  
 Viene illustrato come registrare un VSPackage.  
  
 [Uso di un attributo di registrazione personalizzato per registrare un'estensione](../../misc/using-a-custom-registration-attribute-to-register-an-extension.md)  
 Viene descritto come creare un manifesto di registrazione che può essere utilizzato per distribuire un pacchetto VSPackage gestito.
