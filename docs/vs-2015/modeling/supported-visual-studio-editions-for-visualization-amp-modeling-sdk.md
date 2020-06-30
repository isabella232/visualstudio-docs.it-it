---
title: Edizioni di Visual Studio supportate per l'SDK di visualizzazione e modellazione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
ms.assetid: 7c313ba0-031d-45b8-8220-eead61754747
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3eebefeab6b78955b03d4546a60dd811f5e9ae4e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547654"
---
# <a name="supported-visual-studio-editions-for-visualization-amp-modeling-sdk"></a>Edizioni di Visual Studio supportate per l' &amp; SDK di modellazione della visualizzazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Di seguito sono elencati gli elenchi delle edizioni di Visual Studio supportate con [!INCLUDE[dsl](../includes/dsl-md.md)] negli ambienti di creazione e distribuzione. Per ulteriori informazioni su queste edizioni, vedere il [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [centro per sviluppatori](https://msdn.microsoft.com/vstudio/products/)Microsoft.

## <a name="authoring-edition"></a>Edizione per lo sviluppo
 Per definire un linguaggio specifico di dominio (Domain-Specific Language, DSL) devono essere installati i componenti seguenti:

|Prodotto|Collegamento di download|
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[https://www.visualstudio.com/](https://www.visualstudio.com/)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[SDK di Visual Studio](../extensibility/visual-studio-sdk.md)|
|SDK di visualizzazione e modellazione di Visual Studio|[Download dell'SDK di modellazione](https://www.microsoft.com/download/details.aspx?id=48148)|
## <a name="deployment-editions"></a>Edizioni per la distribuzione
 [!INCLUDE[dsl](../includes/dsl-md.md)]supporta le seguenti configurazioni per la distribuzione dei linguaggi specifici del dominio compilati:

- Visual Studio Enterprise

- Visual Studio Professional

- Pacchetto ridistribuibile Visual Studio Shell (modalità integrata)

- Pacchetto ridistribuibile Visual Studio Shell (modalità isolata)

> [!NOTE]
> Per consentire l'esecuzione di un linguaggio DSL in un prodotto shell, è necessario impostare il campo **supported vs Edition** nel manifesto dell'estensione. Per altre informazioni, vedere [Distribuzione di soluzioni per un linguaggio specifico di dominio](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Vedere anche
 [Glossario di Strumenti Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
