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
ms.openlocfilehash: 227c2871f68545c9f9fe5fa1ea3ceee827ccdc6a
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2020
ms.locfileid: "75917298"
---
# <a name="supported-visual-studio-editions-for-visualization-amp-modeling-sdk"></a>Edizioni di Visual Studio supportate per la visualizzazione &amp; Modeling SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Di seguito sono riportati gli elenchi delle versioni di Visual Studio che sono supportate con [!INCLUDE[dsl](../includes/dsl-md.md)] negli ambienti di creazione e distribuzione. Per ulteriori informazioni su queste edizioni, vedere il centro per [sviluppatori](https://msdn.microsoft.com/vstudio/products/)Microsoft [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

## <a name="authoring-edition"></a>Edizione per lo sviluppo
 Per definire un linguaggio specifico di dominio (Domain-Specific Language, DSL) devono essere installati i componenti seguenti:

|||
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[https://www.visualstudio.com/](https://www.visualstudio.com/)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[Visual Studio SDK](../extensibility/visual-studio-sdk.md)|
|SDK di visualizzazione e modellazione di Visual Studio|[Download dell'SDK di modellazione](https://www.microsoft.com/download/details.aspx?id=48148)|
## <a name="deployment-editions"></a>Edizioni per la distribuzione
 [!INCLUDE[dsl](../includes/dsl-md.md)] supporta le configurazioni seguenti per la distribuzione dei linguaggi specifici di dominio compilati:

- Visual Studio Enterprise

- Visual Studio Professional

- Visual Studio Shell (modalità integrata) pacchetto ridistribuibile

- Pacchetto ridistribuibile Visual Studio Shell (modalità isolata)

> [!NOTE]
> Per rendere un linguaggio DSL può essere eseguita su un prodotto Shell, è necessario impostare il **edizione supportata di Visual Studio** campo nel manifesto dell'estensione. Per altre informazioni, vedere [Distribuzione di soluzioni per un linguaggio specifico di dominio](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Vedere anche
 [Glossario di Strumenti Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
