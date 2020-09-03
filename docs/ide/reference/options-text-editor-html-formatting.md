---
title: Opzioni, Editor di testo, HTML (Web Form), Formattazione
ms.date: 1/15/2019
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.HTML.Format
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9e28caf7f71af7c7a07634d1732a1001a32a4aee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75568321"
---
# <a name="options-text-editor-html-web-forms-formatting"></a>Opzioni, Editor di testo, HTML (Web Form), Formattazione

Usare la pagina di opzioni **Formattazione** per impostare le opzioni di progetto HTML per la formattazione del codice nell'editor del codice. Per accedere a questa pagina, nella barra dei menu scegliere **strumenti**  >  **Opzioni**e quindi espandere formattazione **Text Editor**  >  **HTML (Web Form)** nell'editor di testo  >  **Formatting**.

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
|**Lettere minuscole**|I nomi degli elementi vengono riformattati in minuscolo.|
|**Definizione assembly**|La combinazione di maiuscole e minuscole degli elementi è determinata dalla definizione dell'elemento nella classe di tipo corrispondente.|

**Tag client, Attributi client**

Tramite queste opzioni viene determinato se durante la formattazione automatica i nomi delle proprietà e degli attributi HTML verranno modificati in maiuscolo o minuscolo o se verranno lasciati come immessi.

|Opzione|Risultato|
|---------------------------------|------------------------------|
|**Come immesse**|Esatta combinazione di maiuscole/minuscole dell'attributo come immessa.|
|**Maiuscolo**|I nomi degli attributi vengono riformattati in maiuscolo.|
|**Lettere minuscole**|I nomi degli attributi vengono riformattati in minuscolo.|

## <a name="automatic-formatting-options"></a>Opzioni di formattazione automatica

Tramite queste opzioni viene determinata l'aggiunta o la rimozione delle interruzioni fisiche di riga durante la formattazione automatica nell'editor della visualizzazione Origine. È anche possibile specificare se l'editor racchiude gli attributi tra virgolette.

> [!NOTE]
> Queste impostazioni non alterano gli spazi all'interno del markup XML.

### <a name="uielement-list"></a>Elenco degli elementi di interfaccia

- **Inserisci virgolette per valori attributi durante la digitazione**

   Quando questa opzione è selezionata, l'editor inserisce automaticamente le virgolette per racchiudere gli attributi durante la digitazione, ad esempio: ID = "Select1". Deselezionare questa opzione se si preferisce inserire manualmente le virgolette nel markup.

   > [!NOTE]
   > Indipendentemente dalla selezione di questa opzione, tutte le virgolette esistenti nel markup vengono mantenute: le virgolette non vengono mai rimosse.

- **Inserisci valori di attributo tra virgolette durante la formattazione**

   Quando questa opzione è selezionata, la formattazione automatica aggiunge le virgolette intorno ai valori degli attributi, ad esempio: ID = "Select1".

   > [!NOTE]
   > Indipendentemente dalla selezione di questa opzione, tutte le virgolette esistenti nel markup vengono mantenute.

- **Inserisci automaticamente tag di chiusura**

   Quando questa opzione è selezionata, l'editor crea automaticamente un tag di chiusura, ad esempio, **\</b>** quando si chiude il tag di apertura.

## <a name="tag-wrapping"></a>Ritorno a capo dei tag

Queste opzioni determinano se i tag vengono suddivisi nell'editor in più righe qualora superino una determinata lunghezza.

### <a name="uielement-list"></a>Elenco degli elementi di interfaccia

- **Tag a capo quando superano la lunghezza specificata**

   Se selezionata, nell'editor i tag vengono suddivisi in più righe qualora superino la lunghezza specificata nella casella di testo **Lunghezza**. Questa azione si verifica solo durante la formattazione del tag, non durante la digitazione di un nuovo tag.

   > [!NOTE]
   > Il valore specificato viene considerato come valore minimo. I singoli attributi non vengono suddivisi nell'editor.

- **Lunghezza**

   Viene specificato il numero di caratteri da visualizzare in una riga prima del ritorno a capo. Questa casella di input è disabilitata se non è selezionata la casella **Tag a capo quando superano la lunghezza specificata**.

- **Opzioni specifiche dei tag**

   Viene visualizzata la finestra di dialogo **Opzioni specifiche dei tag**, nella quale è possibile impostare le opzioni di formattazione per i singoli tag o per gruppi di tag.

## <a name="see-also"></a>Vedere anche

- [Generale, ambiente, finestra di dialogo Opzioni](../../ide/reference/general-environment-options-dialog-box.md)
