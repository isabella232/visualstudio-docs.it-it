---
title: 'Procedura: utilizzare frammenti XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3a27375b-81cc-48f6-a884-e1cb8c4f78f5
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4998fbc530cf4350f4a64b0fd527e0764eafce27
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656267"
---
# <a name="how-to-use-xml-snippets"></a>Procedura: utilizzare frammenti XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile richiamare i frammenti XML usando i due comandi seguenti dal menu di scelta rapida dell'editor XML. Il comando **Insert Snippet** inserisce il frammento XML in corrispondenza della posizione del cursore. Il comando **Racchiudi tra** racchiude il frammento XML intorno al testo selezionato. Ogni frammento XML dispone di tipi di frammento designati. I tipi di frammento di codice determinano se il frammento è disponibile con il comando **Inserisci frammento** , il comando **Racchiudi tra** o entrambi.

 Dopo che il frammento XML è stato aggiunto all'editor, i campi modificabili nel frammento vengono evidenziati in giallo e il cursore viene posizionato nel primo campo modificabile.

## <a name="insert-snippet"></a>Inserisci frammento
 Nelle procedure riportate di seguito viene descritto come accedere al comando **Inserisci frammento** .

> [!NOTE]
> Il comando **Inserisci frammento** di codice è disponibile anche tramite il tasto di scelta rapida (CTRL + K, quindi CTRL + X).

#### <a name="to-insert-snippets-from-the-shortcut-menu"></a>Per inserire i frammenti dal menu di scelta rapida

1. Posizionare il cursore nel punto in cui si desidera inserire il frammento XML.

2. Fare clic con il pulsante destro del mouse e scegliere **Inserisci frammento**.

     Viene visualizzato un elenco dei frammenti XML disponibili.

3. Selezionare un frammento dall'elenco usando il mouse, oppure digitare il nome del frammento e premere TAB o INVIO.

#### <a name="to-insert-snippets-using-the-intellisense-menu"></a>Per inserire i frammenti dal menu IntelliSense

1. Posizionare il cursore nel punto in cui si desidera inserire il frammento XML.

2. Scegliere **IntelliSense**dal menu **modifica** e quindi selezionare **Inserisci frammento**di codice.

     Viene visualizzato un elenco dei frammenti XML disponibili.

3. Selezionare un frammento dall'elenco usando il mouse, oppure digitare il nome del frammento e premere TAB o INVIO.

#### <a name="to-insert-snippets-through-the-intellisense-complete-word-list"></a>Per inserire i frammenti dall'elenco Completa parola di IntelliSense

1. Posizionare il cursore nel punto in cui si desidera inserire il frammento XML.

2. Iniziare a digitare il frammento XML che si desidera aggiungere al file. Se il completamento automatico è attivato, viene visualizzato l'elenco Completa parola di IntelliSense. Se l'elenco non viene visualizzato, premere CTRL+BARRA SPAZIATRICE per attivarlo.

3. Selezionare il frammento XML dall'elenco Completa parola.

4. Premere TAB, TAB per richiamare il frammento XML.

> [!NOTE]
> In alcuni casi è possibile che il frammento XML non venga richiamato. Ad esempio, se si tenta di inserire un elemento `xs:complexType` all'interno di un nodo `xs:element`, l'editor non genera alcun frammento XML. Quando un elemento `xs:complexType` viene usato all'interno di un nodo `xs:element`, non vengono rilevati attributi o sottoelementi obbligatori, pertanto l'editor non disporrà di alcun dato da inserire.

#### <a name="to-insert-snippets-using-the-shortcut-name"></a>Per inserire i frammenti dal nome del collegamento

1. Posizionare il cursore nel punto in cui si desidera inserire il frammento XML.

2. Digitare `<` nel riquadro dell'editor.

3. Premere ESC per chiudere l'elenco Completa parola di IntelliSense.

4. Digitare il nome collegamento del frammento, quindi premere TAB per richiamare il frammento XML.

## <a name="surround-with"></a>Racchiudi tra
 Nelle procedure seguenti viene descritto come accedere al comando **Racchiudi tra** .

> [!NOTE]
> Il comando **Racchiudi** tra è disponibile anche tramite il tasto di scelta rapida (CTRL + K, quindi CTRL + S).

#### <a name="to-use-surround-with-from-the-context-menu"></a>Per usare il comando dal menu di scelta rapida

1. Selezionare il testo da racchiudere nell'editor XML.

2. Fare clic con il pulsante destro del mouse e scegliere **Racchiudi tra**.

     Viene visualizzato un elenco delle scelte disponibili con i frammenti XML.

3. Selezionare un frammento dall'elenco usando il mouse, oppure digitare il nome del frammento e premere TAB o INVIO.

#### <a name="to-use-surround-with-from-the-intellisense-menu"></a>Per usare il comando dal menu IntelliSense

1. Selezionare il testo da racchiudere nell'editor XML.

2. Scegliere **IntelliSense**dal menu **modifica** e quindi **Racchiudi**tra.

     Viene visualizzato un elenco delle scelte disponibili con i frammenti XML.

3. Selezionare un frammento dall'elenco usando il mouse, oppure digitare il nome del frammento e premere TAB o INVIO.

## <a name="using-xml-snippets"></a>Utilizzo dei frammenti XML
 Una volta scelto il frammento XML, il testo del frammento di codice viene inserito automaticamente nella posizione del cursore. I campi modificabili del frammento vengono evidenziati e il primo campo modificabile viene selezionato automaticamente. Il campo attualmente selezionato è di tipo boxed.

 Quando si seleziona un campo, è possibile digitare un nuovo valore per tale campo. Premendo TAB è possibile scorrere i campi modificabili del frammento. Premendo MAIUSC+TAB è possibile scorrerli in ordine inverso. Se si fa clic su un campo il cursore viene posizionato all'interno del campo, se si fa doppio clic il campo viene selezionato. Quando un campo è evidenziato, potrebbe essere visualizzata la finestra con la descrizione del campo.

 È modificabile solo la prima istanza di un determinato campo. Quando il campo è evidenziato, le altre istanze del campo sono tratteggiate. Quando si modifica il valore di un campo modificabile, il campo viene modificato ovunque venga usato nel frammento.

 Premere INVIO o ESC per annullare la modifica del campo e tornare alla visualizzazione normale dell'editor.

 I colori predefiniti per i campi dei frammenti di codice modificabili possono essere modificati modificando l'impostazione del campo frammento di codice nel riquadro **tipi di carattere e colori** della finestra di dialogo **Opzioni** . Per altre informazioni, vedere [procedura: modificare i tipi di carattere e i colori nell'editor](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Vedere anche
 [Frammenti XML](../xml-tools/xml-snippets.md) [procedura: generare un frammento XML da uno schema XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md) [procedura: creare frammenti XML](../xml-tools/how-to-create-xml-snippets.md)
