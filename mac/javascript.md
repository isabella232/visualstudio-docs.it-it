---
title: JavaScript e TypeScript
description: Informazioni sul supporto per JavaScript in Visual Studio per Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: 61432695-5B12-4257-B250-48D37EED106D
ms.openlocfilehash: d87af0ad9f19e112740f9bbdc9feffe7e2d794bf9790ee537b9765f6d7a09d08
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121349710"
---
# <a name="javascript-and-typescript-support"></a>Supporto per JavaScript e TypeScript

Visual Studio per Mac offre supporto per JavaScript e TypeScript con evidenziazione della sintassi, formattazione del codice e IntelliSense.

![Supporto per l'editor Typescript](media/tsjseditor-2019.gif)

Per altre informazioni sulla scrittura di JavaScript, vedere le guide [scrittura di codice JavaScript.](/scripting/javascript/writing-javascript-code)

## <a name="adding-a-javascript-file"></a>Aggiunta di un file JavaScript

I file JavaScript vengono quasi sempre aggiunti ai progetti ASP.NET Core tramite la finestra di dialogo **Nuovo file**. Per aggiungere un file JavaScript, fare clic con il pulsante destro del mouse sul progetto e scegliere **Aggiungi > Nuovo file**:

![Aggiunta di nuovi file al progetto](media/javascript-image1.png)

Nella finestra **di dialogo Nuovo file** selezionare Web > file JS **vuoto** o File **TypeScript > web.** Assegnare un nome e quindi scegliere **Nuovo**:

![Creazione di un nuovo file Typescript dal modello](media/javascript-image2.png)

## <a name="intellisense"></a>IntelliSense

Visual Studio per Mac usa il [JavaScript Language Service](/visualstudio/ide/javascript-intellisense) per fornire IntelliSense, consentendo di avere il completamento intelligente del codice, le informazioni sui parametri e gli elenchi di membri durante la scrittura del codice.

JavaScript IntelliSense in Visual Studio per Mac può essere basato sull'inferenza del tipo, JSDoc o dichiarazioni TypeScript.

- **Inferenza del tipo**: il tipo di un oggetto viene dedotto dal contesto del codice circostante. Per altre informazioni, vedere la sezione relativa a Visual Studio in [IntelliSense basato sull'inferenza del tipo](/visualstudio/ide/javascript-intellisense#intellisense-based-on-type-inference).
- **JSDoc**: a volte l'inferenza del tipo non offre le informazioni sul tipo corrette. In questi casi, le informazioni sul tipo possono essere fornite in modo esplicito dalle annotazioni [JSDoc](https://jsdoc.app/about-getting-started.html). Per altre informazioni, vedere la Visual Studio su [IntelliSense basata su JSDoc](/visualstudio/ide/javascript-intellisense#intellisense-based-on-jsdoc)
- **File di dichiarazione TypeScript:** `.d.ts` i file vengono usati per fornire valori per IntelliSense JavaScript. I tipi dichiarati in questo file possono essere usati come tipi nei commenti JSDoc. Per altre informazioni, vedere la sezione relativa a Visual Studio su [IntelliSense basato su file dichiarazione TypeScript](/visualstudio/ide/javascript-intellisense#intellisense-based-on-typescript-declaration-files)

    ![aggiunta di un file di definizione typescript](media/javascript-type-intellisense-2019.gif)

## <a name="see-also"></a>Vedi anche

- [JavaScript IntelliSense (Visual Studio in Windows)](/visualstudio/ide/javascript-intellisense)
