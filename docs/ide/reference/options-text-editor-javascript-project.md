---
title: Opzioni, Editor di testo, JavaScript, Progetto
description: Informazioni su come usare la Project della finestra di dialogo Opzioni per specificare le opzioni di progetto JavaScript e TypeScript nell'editor di codice.
ms.custom: SEO-VS-2020
ms.date: 06/19/2020
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Project.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Project
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Project.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Project
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0b30aaec3087cece63e392cf7170ac85f6be0ad7
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628655"
---
# <a name="options-text-editor-javascript-project"></a>Opzioni, Editor di testo, JavaScript, Progetto

Usare la pagina **Progetto** della finestra di dialogo **Opzioni** per specificare le opzioni di progetto JavaScript e TypeScript nell'editor del codice. Per accedere a questa pagina, sulla barra dei menu scegliere Opzioni strumenti , quindi espandere Editor di testo  >     >  **JavaScript/TypeScript**  >  **Project**.

## <a name="project-analysis-options"></a>Opzioni di analisi progetti

Queste opzioni determinano come l'editor analizza i progetti, genera report di diagnostica e suggerisce miglioramenti. Selezionare o deselezionare le opzioni per specificare come l'editor gestisce queste situazioni.

### <a name="uielement-list"></a>Elenco degli elementi di interfaccia

- **Analizza solo i progetti che contengono file aperti nell'editor**
- **Restituisci dati di diagnostica solo per i file aperti nell'editor**
- **Suggerisci possibili miglioramenti che non sono correzioni**

## <a name="virtual-projects-in-solution-explorer"></a>Progetti virtuali in Esplora soluzioni

Queste opzioni consentono di scegliere se visualizzare progetti virtuali quando una soluzione è caricata o non caricata.

## <a name="compile-on-save"></a>Compila al salvataggio

Queste opzioni determinano se i file TypeScript che non fanno parte del progetto vengono compilati automaticamente. Visual Studio viene compilato usando la versione più recente di TypeScript installata in *C:\Programmi (x86)\Microsoft SDKs\TypeScript*.

Selezionare la casella di controllo e quindi scegliere il tipo di generazione del codice da usare.

### <a name="uielement-list"></a>Elenco degli elementi di interfaccia

- **Usa la generazione del codice AMD per moduli che non fanno parte di un progetto**
- **Usa la generazione del codice CommonJS per moduli che non fanno parte di un progetto**
- **Usa la generazione del codice UMD per moduli che non fanno parte di un progetto**
- **Usa la generazione del codice System per i moduli che non fanno parte di un progetto**
- **Usa la generazione del codice ES2015 per i moduli che non fanno parte di un progetto**

## <a name="ecmascript-version-for-files-that-are-not-part-of-a-project"></a>Versione di ECMAScript per file che non fanno parte di un progetto

Queste opzioni consentono di selezionare la versione di ECMAScript per i file che non fanno parte di un progetto. È possibile scegliere tra **ECMAScript 3**, **ECMAScript 5** o **ECMAScript 6**.

## <a name="jsx-emit-for-tsx-files-that-are-not-part-of-a-project"></a>Creazione JSX per file TSX che non fanno parte di un progetto

Queste opzioni determinano il modo in cui l'editor gestisce i file TypeScript che non fanno parte di un progetto.

### <a name="uielement-list"></a>Elenco degli elementi di interfaccia

|Opzione|Descrizione|
|------------|-----------------|
|**Framework React**|Quando questa opzione è selezionata, l'editor del codice genera un file con estensione *js*.|
|**Preservare**|Quando questa opzione è selezionata, l'editor del codice mantiene JSX come parte dell'output e genera un file con estensione *jsx*.|

## <a name="see-also"></a>Vedi anche

- [Generale, Ambiente, finestra di dialogo Opzioni](../../ide/reference/general-environment-options-dialog-box.md)