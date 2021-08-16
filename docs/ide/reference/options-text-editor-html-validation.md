---
title: Opzioni, Editor di testo, HTML (Web Form), Convalida
description: Informazioni su come usare la pagina Convalida nella sezione HTML per impostare le preferenze per il modo in cui l'editor HTML controlla la sintassi del markup HTML nel documento.
ms.custom: SEO-VS-2020
ms.date: 1/15/2019
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.HTML.Validation
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9266872ef9535802f66d3b068a3f10d51f4270d59de349f53b6547bf79a5afb7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121412218"
---
# <a name="options-text-editor-html-web-forms-validation"></a>Opzioni, Editor di testo, HTML (Web Form), Convalida

Usare la pagina di opzioni **Convalida** per impostare le preferenze relative alla modalità di verifica da parte dell'editor HTML dell'uso della sintassi del markup HTML all'interno del documento. Per accedere a questa pagina, sulla barra dei menu scegliere Opzioni strumenti , quindi espandere Convalida  >  HTML editor di   >  **testo (Web Forms)**  >  .

## <a name="validation"></a>Convalida

- **Utilizza doctype per rilevamento schema di convalida**

   Uno schema determina gli elementi, gli attributi e la combinazione di maiuscole e minuscole validi nello schema in questione. Inoltre, vengono stabiliti i tag e gli attributi che sono disponibili in IntelliSense.

   Selezionare questa opzione se si vuole che in Visual Studio venga usata il contenuto della dichiarazione **<!DOCTYPE>** e dell'elemento **html** della pagina per determinare lo schema. Ad esempio, se si seleziona questa opzione e nella pagina è contenuta la dichiarazione `<!DOCTYPE html>`, Visual Studio usa lo schema HTML5. Tuttavia, se per il tag **html** è presente un attributo **xmlns**, ad esempio `<html xmlns="http://www.w3.org/1999/xhtml">`, Visual Studio usa lo schema XHTML5.

- **Destinazione se doctype non viene trovato**

   Scegliere lo schema in base a cui eseguire la convalida se non vi sono dichiarazioni **<!DOCTYPE>** nella pagina.

  - **Visualizza errori**

     Selezionare la casella di controllo per abilitare la convalida. Se la casella di controllo non è selezionata, l'editor non contrassegna gli errori di convalida.

     Le altre caselle di controllo consentono di ottimizzare la convalida specificando singoli tipi di errore che si vuole vengano contrassegnati dall'editor.

     > [!NOTE]
     > Per alcuni schemi, le opzioni che consentono di contrassegnare singoli tipi di errore non sono disponibili. Ad esempio, se si sceglie **XHTML 1.1** come schema di destinazione, tutte le caselle di controllo vengono disabilitate. In questo caso, vengono contrassegnati tutti i tipi di errori.

## <a name="see-also"></a>Vedi anche

- [Generale, Ambiente, finestra di dialogo Opzioni](../../ide/reference/general-environment-options-dialog-box.md)
