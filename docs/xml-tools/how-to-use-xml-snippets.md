---
title: Come usare frammenti XML
description: Informazioni su come usare i comandi nell'editor XML per inserire frammenti XML o per eseguire il wrapping di un frammento XML intorno al testo selezionato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 3a27375b-81cc-48f6-a884-e1cb8c4f78f5
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: 7a8a46c388286f88739535b17be2e723c5b89f40
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122045476"
---
# <a name="how-to-use-xml-snippets"></a>Procedura: Usare frammenti XML

È possibile richiamare frammenti XML usando i due comandi seguenti nel menu di scelta rapida dell'editor XML. Il **comando Inserisci frammento** inserisce il frammento XML in corrispondenza della posizione del cursore. Il **comando Racchiude tra** racchiude il frammento XML intorno al testo selezionato. Ogni frammento XML dispone di tipi di frammento designati. I tipi di frammento di codice determinano se il frammento è disponibile con il **comando Inserisci** frammento, il **comando Racchiude** tra o entrambi.

Dopo che il frammento XML è stato aggiunto all'editor, i campi modificabili nel frammento vengono evidenziati in giallo e il cursore viene posizionato nel primo campo modificabile.

## <a name="insert-snippet"></a>Inserisci frammento

Le procedure seguenti descrivono come accedere al **comando Inserisci frammento** di codice.

> [!NOTE]
> Il **comando Inserisci frammento** di codice è disponibile anche tramite i tasti di scelta rapida (**CTRL** + **K**, quindi **CTRL** + **X**).

### <a name="to-insert-snippets-from-the-shortcut-menu"></a>Per inserire i frammenti dal menu di scelta rapida

1. Posizionare il cursore nel punto in cui si desidera inserire il frammento XML.

2. Fare clic con il pulsante destro del mouse e **scegliere Inserisci frammento**.

   Viene visualizzato un elenco dei frammenti XML disponibili.

3. Selezionare un frammento di codice dall'elenco usando il mouse oppure digitando il nome del frammento e premendo **TAB** o **INVIO.**

### <a name="to-insert-snippets-using-the-intellisense-menu"></a>Per inserire i frammenti dal menu IntelliSense

1. Posizionare il cursore nel punto in cui si desidera inserire il frammento XML.

2. Scegliere  **IntelliSense** dal menu Modifica e quindi selezionare **Inserisci frammento** di codice.

   Viene visualizzato un elenco dei frammenti XML disponibili.

3. Selezionare un frammento di codice dall'elenco usando il mouse o digitando il nome del frammento e premendo **TAB** o **INVIO.**

### <a name="to-insert-snippets-through-the-intellisense-complete-word-list"></a>Per inserire frammenti di codice tramite l'elenco di parole complete di IntelliSense

1. Posizionare il cursore nel punto in cui si desidera inserire il frammento XML.

2. Iniziare a digitare il frammento XML che si desidera aggiungere al file. Se il completamento automatico è attivato, viene visualizzato l'elenco Completa parola di IntelliSense. Se non viene visualizzato, premere  + **CTRL+BARRA SPAZIATRICE** per attivarlo.

3. Selezionare il frammento XML dall'elenco Completa parola.

4. Premere **TAB,** **TAB per** richiamare il frammento XML.

> [!NOTE]
> In alcuni casi è possibile che il frammento XML non venga richiamato. Ad esempio, se si tenta di inserire un elemento `xs:complexType` all'interno di un nodo `xs:element`, l'editor non genera alcun frammento XML. Quando un elemento `xs:complexType` viene usato all'interno di un nodo `xs:element`, non vengono rilevati attributi o sottoelementi obbligatori, pertanto l'editor non disporrà di alcun dato da inserire.

### <a name="to-insert-snippets-using-the-shortcut-name"></a>Per inserire i frammenti dal nome del collegamento

1. Posizionare il cursore nel punto in cui si desidera inserire il frammento XML.

2. Digitare `<` nel riquadro dell'editor.

3. Premere **ESC per** chiudere l'elenco di parole complete di IntelliSense.

4. Digitare il nome del collegamento del frammento e premere **TAB per** richiamare il frammento XML.

## <a name="surround-with"></a>Racchiudi tra

Le procedure seguenti descrivono come accedere al **comando Surround With** .

> [!NOTE]
> Il **comando Surround With** (Racchiude tra) è disponibile anche tramite i tasti di scelta rapida **(CTRL** + **K,** quindi **CTRL** + **S).**

### <a name="to-use-surround-with-from-the-context-menu"></a>Per usare Surround With (Racchiude tra) dal menu di scelta rapida

1. Selezionare il testo da racchiudere nell'editor XML.

2. Fare clic con il pulsante destro del mouse **e scegliere Surround With (Racchiude tra).**

   Viene visualizzato un elenco delle scelte disponibili con i frammenti XML.

3. Selezionare un frammento di codice dall'elenco usando il mouse oppure digitando il nome del frammento e premendo **TAB** o **INVIO.**

### <a name="to-use-surround-with-from-the-intellisense-menu"></a>Per usare Surround With dal menu IntelliSense

1. Selezionare il testo da racchiudere nell'editor XML.

2. Scegliere  **IntelliSense** dal menu Modifica e quindi selezionare **Racchiude tra.**

   Viene visualizzato un elenco delle scelte disponibili con i frammenti XML.

3. Selezionare un frammento di codice dall'elenco usando il mouse oppure digitando il nome del frammento e premendo **TAB** o **INVIO.**

## <a name="use-xml-snippets"></a>Usare i frammenti XML

Una volta scelto il frammento XML, il testo del frammento di codice viene inserito automaticamente nella posizione del cursore. I campi modificabili del frammento vengono evidenziati e il primo campo modificabile viene selezionato automaticamente. Il campo attualmente selezionato è di tipo boxed.

Quando si seleziona un campo, è possibile digitare un nuovo valore per tale campo. Premendo **TAB** è possibile scorrere i campi modificabili del frammento di codice. Premendo **MAIUSC** + **TAB,** questi vengono spostati in ordine inverso. Se si fa clic su un campo il cursore viene posizionato all'interno del campo, se si fa doppio clic il campo viene selezionato. Quando un campo è evidenziato, potrebbe essere visualizzata la finestra con la descrizione del campo.

È modificabile solo la prima istanza di un determinato campo. Quando il campo è evidenziato, le altre istanze del campo sono tratteggiate. Quando si modifica il valore di un campo modificabile, il campo viene modificato ovunque venga usato nel frammento.

Premendo **INVIO o** **ESC,** la modifica dei campi viene annullata e l'editor torna alla normalità.

I colori predefiniti per i campi dei frammenti  di codice modificabili possono essere modificati modificando l'impostazione Campo frammento di codice nel riquadro Tipi di carattere e colori della **finestra di** dialogo Opzioni.  Per altre informazioni, vedere Procedura: Modificare tipi di [carattere e colori nell'editor.](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md)

## <a name="see-also"></a>Vedi anche

- [frammenti XML](../xml-tools/xml-snippets.md)
- [Procedura: Generare un frammento XML da un XML Schema](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)
- [Procedura: Creare frammenti XML](../xml-tools/how-to-create-xml-snippets.md)
