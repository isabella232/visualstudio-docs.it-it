---
title: Registrazione dei pacchetti VSPackage | Microsoft Docs
description: Un file con estensione pkgdef contiene informazioni che altrimenti verrebbero aggiunte al Registro di sistema. Informazioni su Visual Studio usa i file con estensione pkgdef per descrivere/individuare un VSPackage.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709508"
---
# <a name="registering-vspackages"></a>Registrazione di pacchetti VSPackage
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] si basa sui file con estensione pkgdef per descrivere e individuare un VSPackage. Un file con estensione pkgdef contiene tutte le informazioni di registrazione che altrimenti verrebbero aggiunte al Registro di sistema. I pacchetti VSPackage gestiti vengono registrati aggiungendo attributi al codice sorgente e quindi eseguendo l'utilità [CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) nell'assembly risultante per generare un file con estensione pkgdef.

## <a name="in-this-section"></a>Contenuto della sezione
- [Definizione del percorso di file VSPackage nella shell di Visual Studio](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)

 Descrive il percorso di caricamento per i pacchetti VSPackage.

- [Registrazione e annullamento della registrazione di pacchetti VSPackage](../../extensibility/registering-and-unregistering-vspackages.md)

 Viene illustrato come registrare un VSPackage.
