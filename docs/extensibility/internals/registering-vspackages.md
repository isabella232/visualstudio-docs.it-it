---
title: Registrazione di VSPackage Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b40793a5ab317b6a467e55df13302f19cec82640
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705738"
---
# <a name="registering-vspackages"></a>Registrazione di pacchetti VSPackage
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]si basa su file con estensione pkgdef per descrivere e individuare un pacchetto VSPackage. Un file .pkgdef contiene tutte le informazioni di registrazione che altrimenti verrebbero aggiunte al Registro di sistema. VsPackage gestiti vengono registrati aggiungendo attributi al codice sorgente e quindi eseguendo [l'utilità CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) sull'assembly risultante per generare un file pkgdef.

## <a name="in-this-section"></a>Contenuto della sezione
- [Definizione del percorso di file VSPackage nella shell di Visual Studio](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)

 Descrive il percorso di caricamento per i package VS.

- [Registrazione e annullamento della registrazione di pacchetti VSPackage](../../extensibility/registering-and-unregistering-vspackages.md)

 Viene illustrato come registrare un pacchetto VSPackage.Explains how to register a VSPackage.
