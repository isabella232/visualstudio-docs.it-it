---
title: Proprietà dei documenti XML, finestra Proprietà
ms.date: 03/05/2019
ms.topic: reference
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 679ac529708a49d18025672ce8f880c4f7710471
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526269"
---
# <a name="xml-document-properties-properties-window"></a>Proprietà di documento XML, finestra proprietà

Il **proprietà** finestra fornisce informazioni di base relative al documento attivo nell'editor XML. Le proprietà disponibili variano in base al tipo di documento XML correntemente attivo.

> [!NOTE]
> Tutte le proprietà del documento XML vengono salvate nella soluzione. Di conseguenza, non sarà necessario immettere nuovamente tali valori alla successiva apertura della soluzione.

**Codifica**

La codifica dei caratteri per il file. Modificando questa proprietà si modifica anche l'attributo della codifica nella dichiarazione XML e viceversa. La nuova codifica viene utilizzata per codificare il file quando si salva il file.

**Input**

Il documento di input associato al foglio di stile XSLT. Viene usato per il **avviare XSLT** comandi, ad esempio, **XML** > **avvia XSLT senza debug**. Un documento può essere selezionato utilizzando il pulsante Sfoglia (**...** ) pulsante.

Questa proprietà è visibile solo quando un file XSLT viene aperto nell'editor.

**Output**

Il file che viene generato durante la trasformazione di un documento XML.

Se non viene specificato un file, viene generato un nome di file predefinito in base il `method` attributo la `xsl:output` elemento, che determina l'estensione di file. Il file predefinito si trova nella directory temporanea dell'utente corrente.

**Schemi**

Gli schemi da usare per la convalida. Il pulsante apre il **schemi XSD** nella finestra di dialogo può essere usata per selezionare gli schemi da usare.

È possibile anche immettere il percorso degli schemi. Se vengono specificati più schemi, ogni singolo percorso di schema deve essere racchiuso tra virgolette.

**Foglio di stile**

Il file XSLT utilizzato per trasformare il documento quando la **avviare il debug di XSLT** e **avviare senza debug XSLT** vengono utilizzati i comandi. Se questo campo è vuoto, l'editor Usa il valore fornito nel `xml-stylesheet` istruzione del documento o di elaborazione viene richiesto un nome di file.

Quando si modifica un file XSLT, questa proprietà può essere utilizzata per specificare che deve essere un foglio di stile utilizzato quando la **avviare il debug di XSLT** o **avvia XSLT senza debug** comando selezionato. Ad esempio, è possibile eseguire questa operazione quando si sta modificando un foglio di stile incluso in un foglio di stile padre.

## <a name="see-also"></a>Vedere anche

- [Editor XML](../xml-tools/xml-editor.md)