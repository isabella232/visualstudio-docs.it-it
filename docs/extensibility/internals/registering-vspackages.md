---
title: Registrazione di pacchetti VSPackage | Microsoft Docs
description: Un file con estensione pkgdef contiene informazioni che altrimenti verrebbero aggiunte al Registro di sistema. Informazioni su Visual Studio file con estensione pkgdef per descrivere/individuare un VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: b8f4f56bd2f033501e8482fbd813aa72e1cb2bf9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122062875"
---
# <a name="registering-vspackages"></a>Registrazione di pacchetti VSPackage
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] si basa su file con estensione pkgdef per descrivere e individuare un VSPackage. Un file con estensione pkgdef contiene tutte le informazioni di registrazione che altrimenti verrebbero aggiunte al Registro di sistema. I PACCHETTI VSPackage gestiti vengono registrati aggiungendo attributi al codice sorgente e quindi eseguendo l'utilità [CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) nell'assembly risultante per generare un file con estensione pkgdef.

## <a name="in-this-section"></a>Contenuto della sezione
- [Definizione del percorso di file VSPackage nella shell di Visual Studio](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)

 Descrive il percorso di caricamento per i pacchetti VSPackage.

- [Registrazione e annullamento della registrazione di pacchetti VSPackage](../../extensibility/registering-and-unregistering-vspackages.md)

 Viene illustrato come registrare un VSPackage.
