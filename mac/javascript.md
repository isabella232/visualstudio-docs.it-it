---
title: Javascript
description: Informazioni sul supporto per Javascript in Visual Studio per Mac
author: conceptdev
ms.author: crdun
ms.date: 05/03/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 61432695-5B12-4257-B250-48D37EED106D
ms.openlocfilehash: 6efc22f916973f292daa97bdd6b5129ac9311f04
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2018
ms.locfileid: "48881072"
---
# <a name="javascript-support"></a>Supporto per JavaScript

Visual Studio per Mac offre supporto per Javascript e Typescript attraverso evidenziazione della sintassi, formattazione del codice e IntelliSense. 

![Supporto per l'editor Typescript](https://msdnshared.blob.core.windows.net/media/2018/03/TypeScript-editor.gif)

Per altre informazioni sulla scrittura di codice JavaScript, vedere le guide [Scrittura di codice JavaScript](https://docs.microsoft.com/scripting/javascript/writing-javascript-code).

## <a name="adding-a-javascript-file"></a>Aggiunta di un file JavaScript

I file JavaScript vengono quasi sempre aggiunti ai progetti ASP.NET Core tramite la finestra di dialogo **Nuovo file**. Per aggiungere un file JavaScript, fare clic con il pulsante destro del mouse sul progetto e scegliere **Aggiungi > Nuovo file**: 

![Aggiunta di nuovi file al progetto](media/javascript-image1.png)

Nella finestra di dialogo Nuovo file selezionare **Web > File JavaScript vuoto** oppure **Web > File TypeScript**. Assegnare un nome e quindi scegliere **Nuovo**:

![Creazione di un nuovo file Typescript dal modello](media/javascript-image2.png)

## <a name="intellisense"></a>IntelliSense

Visual Studio per Mac usa [Javascript Language Service](/visualstudio/ide/javascript-intellisense) per rendere disponibile Intellisense che offre il completamento intelligente del codice, informazioni sui parametri ed elenchi membri durante la scrittura di codice.

Javascript Intellisense in Visual Studio per Mac può essere basato sull'inferenza del tipo, su JSDoc o sulla dichiarazione Typescript.

- **Inferenza del tipo**: il tipo di un oggetto viene dedotto dal contesto del codice circostante. Per altre informazioni, vedere la sezione relativa a Visual Studio in [IntelliSense basato sull'inferenza del tipo](https://docs.microsoft.com/visualstudio/ide/javascript-intellisense#intellisense-based-on-type-inference).
- **JSDoc**: a volte l'inferenza del tipo non offre le informazioni sul tipo corrette. In questi casi, le informazioni sul tipo possono essere fornite in modo esplicito dalle annotazioni [JSDoc](http://usejsdoc.org/about-getting-started.html). Per altre informazioni, vedere la sezione relativa a Visual Studio in [Intellisense basato su JSDoc](https://docs.microsoft.com/visualstudio/ide/javascript-intellisense#intellisense-based-on-jsdoc)
- **File di dichiarazione TypeScript**: per specificare i valori per Javascript Intellisense vengono usati file `.d.ts`. I tipi dichiarati in questo file possono essere usati come tipi nei commenti JSDoc. Per altre informazioni, vedere la sezione relativa a Visual Studio in [IntelliSense basato su file dichiarazione TypeScript](https://docs.microsoft.com/visualstudio/ide/javascript-intellisense#intellisense-based-on-typescript-declaration-files) ![Aggiunta di un file di definizione Typescript](media/javascript-image3.png)