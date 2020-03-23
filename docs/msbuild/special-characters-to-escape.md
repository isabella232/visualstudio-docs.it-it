---
title: Caratteri speciali di escape | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- special characters to escape
- msbuild, special characters to escape
ms.assetid: 5b5172c3-41e4-4f38-a16f-2aeac831a5fc
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1b17ded468e262d4f636ed5494081adab7b8c5f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632251"
---
# <a name="special-characters-to-escape"></a>Caratteri speciali di escape

I caratteri speciali devono essere preceduto da un carattere di escape solo se hanno un significato speciale nel contesto in cui vengono usati. Ad esempio, l'asterisco (*) è un carattere speciale solo negli attributi "Include" ed "Exclude" di una definizione di elemento o in una chiamata a <xref:Microsoft.Build.Tasks.CreateItem>. In tutti gli altri casi, l'asterisco viene considerato come un asterisco letterale. Nonostante non sia necessario usare il carattere di escape davanti agli asterischi in ogni parte dei file di progetto, l'operazione non causa problemi.

 Usare la notazione %\<xx> al posto del carattere speciale, dove \<xx> rappresenta il valore esadecimale del carattere ASCII. Ad esempio, per usare un asterisco (*) come carattere letterale, usare il valore `%2A`.

 Di seguito è riportato l'elenco completo dei caratteri speciali di escape:

|Carattere|Descrizione|
|---------------|-----------------|
|%|Segno di percentuale, usato per fare riferimento a metadati.|
|$|Segno di dollaro, usato per fare riferimento alle proprietà.|
|@|Chiocciola, usata per fare riferimento agli elenchi di elementi.|
|(|Parentesi di apertura, usata negli elenchi.|
|)|Parentesi di chiusura, usata negli elenchi.|
|;|Punto e virgola, separatore di elenco.|
|?|Punto interrogativo, un carattere jolly usato nel descrivere le specifiche di un file nella sezione Include/Exclude di un elemento.|
|*|Asterisco, un carattere jolly usato nel descrivere le specifiche di un file nella sezione Include/Exclude di un elemento.|

> [!NOTE]
> In alcuni scenari, potrebbe essere necessario eseguire l'escape dei `Exec` caratteri di virgolette doppie ("), ad esempio quando si utilizza all'interno di un'attività.

## <a name="see-also"></a>Vedere anche

- [Procedura: eseguire l'escape di caratteri speciali in MSBuildHow to: Escape special characters in MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md)
- [Informazioni di riferimento su MSBuild](../msbuild/msbuild-reference.md)
