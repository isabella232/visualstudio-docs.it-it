---
title: Organizzazione gerarchica di risorse per la localizzazione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- resource files, localized
- localization [Visual Studio], resources
- fallback resources
- international applications [Visual Studio], storing resources
- satellite assemblies, resource hierarchies
- globalization [Visual Studio], resources
- satellite assemblies
- resources [Visual Studio], fallback system
- resource files, fallback processes
ms.assetid: dadf8f2c-f74c-44d7-bec0-a1e956d8d38d
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0a79caca18c7813605ff851eea6bda642e6300a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645619"
---
# <a name="hierarchical-organization-of-resources-for-localization"></a>Organizzazione gerarchica di risorse per la localizzazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio, le risorse localizzate (dati come stringhe e immagini specifiche di ogni impostazione cultura) vengono archiviate in file separati e caricate in base alle impostazioni cultura dell'interfaccia utente. Per comprendere come vengono caricate le risorse localizzate, è utile pensarle come organizzate in modo gerarchico.

## <a name="kinds-of-resources-in-the-hierarchy"></a>Tipi di risorse nella gerarchia

- Nella parte superiore della gerarchia si trovano le risorse di fallback per le impostazioni cultura predefinite, ad esempio inglese ("en"). Queste sono le uniche risorse che non dispongono di un proprio file. Vengono archiviate nell'assembly principale.

- Sotto le risorse di fallback si trovano le risorse per le impostazioni cultura non associate ad alcun paese. Alcune impostazioni cultura non associate ad alcun paese sono associate a una lingua, ma non a un paese/area geografica. Ad esempio, "fr" per il francese rappresenta impostazioni cultura non associate ad alcun paese. Si noi che le risorse di fallback sono disponibili anche per le impostazioni cultura non associate ad alcun paese e per uno in particolare.

- Sotto a queste risorse si trovano quelle per le impostazioni cultura specifiche. Un'impostazione cultura specifica è associata a una lingua e a un paese/regione. Ad esempio, il francese canadese ("fr-CA") è un'impostazione cultura specifica.

  Se un'applicazione tenta di caricare una risorsa localizzata, ad esempio una stringa, e non la trova, dovrà risalire la gerarchia finché trova un file di risorse contenente la risorsa richiesta.

  Il modo migliore per memorizzare le risorse consiste nel renderle il più generali possibile. Pertanto, quando possibile, è opportuno memorizzare stringhe, immagini e altre risorse localizzate nei file di risorse per le impostazioni cultura non associate ad alcun paese anziché in quelli per le impostazioni cultura specifiche. Ad esempio, se si dispone di risorse per le impostazioni cultura del francese belga ("fr-BE") e le risorse immediatamente sopra sono le risorse di fallback in inglese, può verificarsi un problema quando si tenta di usare l'applicazione su un sistema configurato per le impostazioni cultura del francese canadese. Il sistema cercherà un assembly satellite "fr-CA", non lo troverà e caricherà l'assembly principale che contiene la risorsa di fallback, ovvero l'inglese, invece di caricare le risorse per il francese. L'immagine seguente illustra questo spiacevole scenario.

  ![Solo risorse specifiche](../ide/media/vbspecificresourcesonly.gif "vbSpecificResourcesOnly")

  Se si segue la procedura consigliata di inserimento di più risorse possibili in un file di risorse con impostazioni cultura non associate ad alcun paese per le impostazioni cultura "fr", l'utente francese canadese non visualizzerà le risorse contrassegnate per le impostazioni cultura "fr-BE", ma visualizzerà le stringhe in francese. L'immagine seguente illustra questo scenario più favorevole.

  ![Grafica NeutralSpecificResources](../ide/media/vbneutralspecificresources.gif "vbNeutralSpecificResources")

## <a name="see-also"></a>Vedere anche
 [Lingue di risorse neutre per la](../ide/neutral-resources-languages-for-localization.md) [sicurezza di localizzazione e gli assembly satellite localizzati](../ide/security-and-localized-satellite-assemblies.md) [localizzazione di applicazioni](../ide/localizing-applications.md) globalizzazione [e localizzazione di applicazioni](../ide/globalizing-and-localizing-applications.md) [procedura: impostare le impostazioni cultura e le impostazioni cultura dell'interfaccia utente per Windows Forms globalizzazione](https://msdn.microsoft.com/694e049f-0b91-474a-9789-d35124f248f0) [procedura: impostare le impostazioni cultura e le impostazioni cultura dell'interfaccia utente per la globalizzazione della pagina Web ASP.NET](https://msdn.microsoft.com/library/76091f86-f967-4687-a40f-de87bd8cc9a0)
