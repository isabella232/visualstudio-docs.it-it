---
title: Registrazione di pacchetti VSPackage | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 786522d32680a66aa0f74cf0111c3e98708cce91
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51727890"
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

