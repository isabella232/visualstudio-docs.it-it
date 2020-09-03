---
title: Registrazione delle estensioni di file per le distribuzioni side-by-side | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 354b91dd1282df9726c1ee9c47f610b0dfdd9c1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163691"
---
# <a name="registering-file-name-extensions-for-side-by-side-deployments"></a>Registrazione delle estensioni per le distribuzioni side-by-side
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per i pacchetti VSPackage distribuiti in un ambiente affiancato, è necessario registrare le estensioni dei nomi di file per associare i file alla versione corretta di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . A meno che non si usi un'estensione di file specifica della versione, la registrazione consente agli utenti di aprire i file di progetto e degli elementi di progetto nella versione appropriata di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Informazioni sulle estensioni di file](../extensibility/about-file-name-extensions.md)  
 Viene illustrato come vengono registrate le estensioni di file.  
  
 [Definizione dei gestori di file per le estensioni di file](../extensibility/specifying-file-handlers-for-file-name-extensions.md)  
 Vengono fornite informazioni su come registrare le applicazioni in grado di aprire, modificare e così via, una particolare estensione di file.  
  
 [Registrazione di verbi per le estensioni di file](../extensibility/registering-verbs-for-file-name-extensions.md)  
 Viene illustrato come registrare i verbi.  
  
 [Gestione delle associazioni di file side-by-side](../extensibility/managing-side-by-side-file-associations.md)  
 Viene illustrato come gestire installazioni affiancate in cui è necessario richiamare una particolare versione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] per aprire un file.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Supporto di più versioni di Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)  
 Descrive i problemi relativi alla presenza di più versioni di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e ai VSPackage durante lo sviluppo e la distribuzione agli utenti finali.
