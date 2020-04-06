---
title: Registrazione delle estensioni dei nomi di file per le distribuzioni side-by-side Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701546"
---
# <a name="register-file-name-extensions-for-side-by-side-deployments"></a>Registrare le estensioni dei nomi di file per le distribuzioni side-by-sideRegister file name extensions for side-by-side deployments
Per i package VS distribuiti in un ambiente side-by-side, è necessario registrare le estensioni di file per associare i file alla versione corretta di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. A meno che non si utilizzi un'estensione di file specifica della versione, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]la registrazione consente agli utenti di aprire i file del progetto e dell'elemento di progetto nella versione appropriata di .

## <a name="in-this-section"></a>Contenuto della sezione
- [Informazioni sulle estensioni di file](../extensibility/about-file-name-extensions.md) Viene illustrato come vengono registrate le estensioni di file.

- [Specificare i gestori di file per le estensioni di fileSpecify file handlers for file name extensions](../extensibility/specifying-file-handlers-for-file-name-extensions.md) Vengono fornite informazioni su come registrare le applicazioni che possono aprire, modificare e così via, una particolare estensione di file.

- [Registrare i verbi per le estensioni di fileRegister verbs for file name extensions](../extensibility/registering-verbs-for-file-name-extensions.md) Viene illustrato come registrare i verbi.

- [Gestire le associazioni di file side-by-side](../extensibility/managing-side-by-side-file-associations.md) Viene illustrato come gestire le installazioni side-by-side in cui una particolare versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] deve essere richiamata per aprire un file.

## <a name="related-sections"></a>Sezioni correlate
- [Supportare più versioni di Visual StudioSupport multiple versions of Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md) Vengono descritti i problemi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] relativi a più versioni di e il pacchetto VSPackage durante lo sviluppo e la distribuzione agli utenti finali.
