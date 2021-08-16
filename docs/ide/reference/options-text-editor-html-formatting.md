---
title: Opzioni, Editor di testo, HTML (Web Form), Formattazione
description: Informazioni su come usare la pagina Formattazione nella sezione HTML per impostare le opzioni di progetto HTML per la formattazione del codice nell'editor di codice.
ms.custom: SEO-VS-2020
ms.date: 1/15/2019
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.HTML.Format
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 22e4d986204645e136709efad87e27b5b97289ec0d6042d8bc03cbfbcd9fb9ee
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121271914"
---
# <a name="options-text-editor-html-web-forms-formatting"></a>Opzioni, Editor di testo, HTML (Web Form), Formattazione

Usare la pagina di opzioni **Formattazione** per impostare le opzioni di progetto HTML per la formattazione del codice nell'editor del codice. Per accedere a questa pagina, sulla barra dei menu scegliere Opzioni strumenti , quindi espandere Html editor di testo  >     >  **(Web Forms)**  >  **Formattazione**.

## <a name="capitalization"></a>Uso delle maiuscole

Se queste opzioni sono selezionate, nella visualizzazione Origine e negli editor XML verrà applicato un formato predefinito per i caratteri maiuscoli e minuscoli ai nomi di elementi e attributi al momento della creazione degli elementi e durante la formattazione automatica. Le impostazioni in **Applica formattazione automatica** determinano il momento in cui viene eseguita la riformattazione automatica.

> [!WARNING]
> Nel linguaggio XML viene fatta distinzione tra maiuscole e minuscole. L'impostazione di un formato predefinito per i caratteri maiuscoli e minuscoli può influire sui parser XML.

### <a name="uielement-list"></a>Elenco degli elementi di interfaccia

**Tag server, Attributi server**

Queste opzioni specificano la modalità di applicazione delle lettere maiuscole e minuscole nel markup dei controlli server Web.

|Opzione|Risultato|
|---------------------------------|------------------------------|
|**Come immesse**|Esatta combinazione di maiuscole/minuscole dell'elemento come immessa.|
|**Maiuscolo**|I nomi degli elementi vengono riformattati in maiuscolo.|
|**Minuscolo**|I nomi degli elementi vengono riformattati in minuscolo.|
|**Definizione assembly**|La combinazione di maiuscole e minuscole degli elementi è determinata dalla definizione dell'elemento nella classe di tipo corrispondente.|

**Tag client, Attributi client**

Tramite queste opzioni viene determinato se durante la formattazione automatica i nomi delle proprietà e degli attributi HTML verranno modificati in maiuscolo o minuscolo o se verranno lasciati come immessi.

|Opzione|Risultato|
|---------------------------------|------------------------------|
|**Come immesse**|Esatta combinazione di maiuscole/minuscole dell'attributo come immessa.|
|**Maiuscolo**|I nomi degli attributi vengono riformattati in maiuscolo.|
|**Minuscolo**|I nomi degli attributi vengono riformattati in minuscolo.|

## <a name="automatic-formatting-options"></a>Opzioni di formattazione automatica

Tramite queste opzioni viene determinata l'aggiunta o la rimozione delle interruzioni fisiche di riga durante la formattazione automatica nell'editor della visualizzazione Origine. È anche possibile specificare se l'editor racchiude gli attributi tra virgolette.

> [!NOTE]
> Queste impostazioni non alterano gli spazi all'interno del markup XML.

### <a name="uielement-list"></a>Elenco degli elementi di interfaccia

- **Inserisci virgolette per valori attributi durante la digitazione**

   Quando questa opzione è selezionata, l'editor inserisce automaticamente le virgolette intorno agli attributi durante la digitazione(ad esempio: ID="Select1"). Deselezionare questa opzione se si preferisce inserire manualmente le virgolette nel markup.

   > [!NOTE]
   > Indipendentemente dalla selezione di questa opzione, tutte le virgolette esistenti nel markup vengono mantenute: le virgolette non vengono mai rimosse.

- **Inserisci valori di attributo tra virgolette durante la formattazione**

   Quando questa opzione è selezionata, la formattazione automatica aggiunge le virgolette intorno ai valori degli attributi (ad esempio: ID="Select1").

   > [!NOTE]
   > Indipendentemente dalla selezione di questa opzione, tutte le virgolette esistenti nel markup vengono mantenute.

- **Inserisci automaticamente tag di chiusura**

   Quando questa opzione è selezionata, l'editor crea automaticamente un tag di chiusura ,ad esempio , quando **\</b>** si chiude il tag di apertura.

## <a name="tag-wrapping"></a>Ritorno a capo dei tag

Queste opzioni determinano se i tag vengono suddivisi nell'editor in più righe qualora superino una determinata lunghezza.

### <a name="uielement-list"></a>Elenco degli elementi di interfaccia

- **Tag a capo quando superano la lunghezza specificata**

   Se selezionata, nell'editor i tag vengono suddivisi in più righe qualora superino la lunghezza specificata nella casella di testo **Lunghezza**. Questa azione si verifica solo durante la formattazione del tag, non durante la digitazione di un nuovo tag.

   > [!NOTE]
   > Il valore specificato viene considerato come valore minimo. I singoli attributi non vengono suddivisi nell'editor.

- **Length**

   Viene specificato il numero di caratteri da visualizzare in una riga prima del ritorno a capo. Questa casella di input è disabilitata se non è selezionata la casella **Tag a capo quando superano la lunghezza specificata**.

- **Opzioni specifiche dei tag**

   Viene visualizzata la finestra di dialogo **Opzioni specifiche dei tag**, nella quale è possibile impostare le opzioni di formattazione per i singoli tag o per gruppi di tag.

## <a name="see-also"></a>Vedi anche

- [Generale, Ambiente, finestra di dialogo Opzioni](../../ide/reference/general-environment-options-dialog-box.md)
