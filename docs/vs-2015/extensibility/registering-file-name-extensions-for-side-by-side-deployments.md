---
title: La registrazione di estensioni di File per le distribuzioni Side-By-Side | Microsoft Docs
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
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d0312bbc7bd6c73cf0141157cde13f0a381f5e41
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51805671"
---
# <a name="registering-file-name-extensions-for-side-by-side-deployments"></a>Registrazione delle estensioni per le distribuzioni side-by-side
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per i pacchetti VSPackage distribuiti in un ambiente side-by-side, è necessario registrare le estensioni di file per associare i file con la versione corretta di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. A meno che non si usa un'estensione di file specifici della versione, la registrazione consente agli utenti di aprire il progetto e file di elementi nella versione appropriata del progetto [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="in-this-section"></a>In questa sezione  
 [Informazioni sulle estensioni di file](../extensibility/about-file-name-extensions.md)  
 Viene descritto come estensioni di file registrate.  
  
 [Definizione dei gestori di file per le estensioni di file](../extensibility/specifying-file-handlers-for-file-name-extensions.md)  
 Vengono fornite informazioni su come registrare le applicazioni che possono essere aperti, modifica e così via, un'estensione particolare.  
  
 [Registrazione di verbi per le estensioni di file](../extensibility/registering-verbs-for-file-name-extensions.md)  
 Viene descritto come registrare i verbi.  
  
 [Gestione delle associazioni di file side-by-side](../extensibility/managing-side-by-side-file-associations.md)  
 Descrive come gestire le installazioni side-by-side in cui una determinata versione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] deve essere richiamato per aprire un file.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Supporto di più versioni di Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)  
 Descrive i problemi relativi alla presenza di più versioni di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e ai VSPackage durante lo sviluppo e la distribuzione agli utenti finali.

