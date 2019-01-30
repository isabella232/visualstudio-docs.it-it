---
title: Organizzazione gerarchica di risorse per la localizzazione
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4df50f1336f235d50d7c897deb2450469f9128b8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55038604"
---
# <a name="hierarchical-organization-of-resources-for-localization"></a>Organizzazione gerarchica di risorse per la localizzazione

In Visual Studio, le risorse localizzate (dati come stringhe e immagini specifiche di ogni impostazione cultura) vengono archiviate in file separati e caricate in base alle impostazioni cultura dell'interfaccia utente. Per comprendere come vengono caricate le risorse localizzate, è utile pensarle come organizzate in modo gerarchico.

## <a name="kinds-of-resources-in-the-hierarchy"></a>Tipi di risorse nella gerarchia

- Nella parte superiore della gerarchia si trovano le risorse di fallback per le impostazioni cultura predefinite, ad esempio inglese ("en"). Queste sono le uniche risorse che non dispongono di un proprio file. Vengono archiviate nell'assembly principale.

- Sotto le risorse di fallback si trovano le risorse per le impostazioni cultura non associate ad alcun paese. Alcune impostazioni cultura non associate ad alcun paese sono associate a una lingua, ma non a un paese/area geografica. Ad esempio, "fr" per il francese rappresenta impostazioni cultura non associate ad alcun paese. Le risorse di fallback sono disponibili anche per le impostazioni cultura non associate ad alcun paese e per uno in particolare.

- Sotto le risorse delle impostazioni cultura non associate ad alcun paese si trovano quelle per le impostazioni cultura specifiche. Un'impostazione cultura specifica è associata a una lingua e a un paese/area geografica. Ad esempio, il francese canadese ("fr-CA") è un'impostazione cultura specifica.

Se un'applicazione tenta di caricare una risorsa localizzata, ad esempio una stringa, e non la trova, dovrà risalire la gerarchia finché trova un file di risorse contenente la risorsa richiesta.

Il modo migliore per memorizzare le risorse consiste nel renderle il più generali possibile. Pertanto, quando possibile, è opportuno memorizzare stringhe, immagini e altre risorse localizzate nei file di risorse per le impostazioni cultura non associate ad alcun paese anziché in quelli per le impostazioni cultura specifiche. Ad esempio, se si dispone di risorse per le impostazioni cultura del francese belga ("fr-BE") e le risorse immediatamente sopra sono le risorse di fallback in inglese, può verificarsi un problema quando si tenta di usare l'applicazione su un sistema configurato per le impostazioni cultura del francese canadese. Il sistema cercherà un assembly satellite "fr-CA", ma non lo troverà e caricherà l'assembly principale che contiene la risorsa di fallback, ovvero l'inglese, invece di caricare le risorse per il francese. L'immagine seguente illustra questo spiacevole scenario.

![Solo risorse specifiche](../ide/media/vbspecificresourcesonly.gif)

Se si segue la procedura consigliata di inserimento di più risorse possibili in un file di risorse con impostazioni cultura non associate ad alcun paese per le impostazioni cultura "fr", l'utente francese canadese non visualizzerà le risorse contrassegnate per le impostazioni cultura "fr-BE", ma visualizzerà le stringhe in francese. L'immagine seguente illustra questo scenario più favorevole.

![Grafica NeutralSpecificResources](../ide/media/vbneutralspecificresources.gif)

## <a name="see-also"></a>Vedere anche

- [Lingue di risorse non associate ad alcun paese per la localizzazione](../ide/neutral-resources-languages-for-localization.md)
- [Sicurezza e assembly satellite localizzati](../ide/security-and-localized-satellite-assemblies.md)
- [Localizzazione di applicazioni](../ide/localizing-applications.md)
- [Globalizzazione e localizzazione di applicazioni](../ide/globalizing-and-localizing-applications.md)