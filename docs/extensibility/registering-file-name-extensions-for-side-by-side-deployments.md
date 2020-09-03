---
title: Registrazione delle estensioni di file per le distribuzioni side-by-side | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6717625a44b48a25d293f68d01cd9fa3c7c24853
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701546"
---
# <a name="register-file-name-extensions-for-side-by-side-deployments"></a>Registrare le estensioni di file per le distribuzioni side-by-side
Per i pacchetti VSPackage distribuiti in un ambiente affiancato, è necessario registrare le estensioni dei nomi di file per associare i file alla versione corretta di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . A meno che non si usi un'estensione di file specifica della versione, la registrazione consente agli utenti di aprire i file di progetto e degli elementi di progetto nella versione appropriata di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="in-this-section"></a>Contenuto della sezione
- [Informazioni sulle estensioni di file](../extensibility/about-file-name-extensions.md) Viene illustrato come vengono registrate le estensioni di file.

- [Specificare i gestori di file per le estensioni di file](../extensibility/specifying-file-handlers-for-file-name-extensions.md) Vengono fornite informazioni su come registrare le applicazioni in grado di aprire, modificare e così via, una particolare estensione di file.

- [Registrare i verbi per le estensioni dei nomi di file](../extensibility/registering-verbs-for-file-name-extensions.md) Viene illustrato come registrare i verbi.

- [Gestire le associazioni di file affiancati](../extensibility/managing-side-by-side-file-associations.md) Viene illustrato come gestire installazioni affiancate in cui è necessario richiamare una particolare versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per aprire un file.

## <a name="related-sections"></a>Sezioni correlate
- [Supporto di più versioni di Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md) Vengono descritti i problemi relativi a più versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e al pacchetto VSPackage durante lo sviluppo e la distribuzione agli utenti finali.
