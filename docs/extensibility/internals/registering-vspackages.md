---
title: Registrazione di pacchetti VSPackage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc8082d63376abeab2da0e8fa7b999c12195d4e7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55006073"
---
# <a name="registering-vspackages"></a>Registrazione di pacchetti VSPackage
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] si basa sui file con estensione pkgdef per descrivere e individuare un pacchetto VSPackage. Un file con estensione pkgdef contiene tutte le informazioni di registrazione che altrimenti verrebbero aggiunti al Registro di sistema. I VSPackage gestiti sono registrati aggiungendo attributi al codice sorgente e quindi eseguendo il [utilità CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) sull'assembly risultante per generare un file. pkgdef.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Definizione del percorso di file VSPackage nella shell di Visual Studio](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Descrive il percorso di caricamento per i pacchetti VSPackage.  
  
 [Registrazione e annullamento della registrazione di pacchetti VSPackage](../../extensibility/registering-and-unregistering-vspackages.md)  
 Viene illustrato come registrare un VSPackage.  
