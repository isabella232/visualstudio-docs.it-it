---
title: Proprietà dei documenti XML, finestra Proprietà
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 69cd8a8f1acd650c65c995f303adc4d3ee2c1bc5
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55938244"
---
# <a name="xml-document-properties-properties-window"></a>Proprietà di documento XML, finestra proprietà

Il **proprietà** finestra fornisce informazioni di base relative al documento attivo nell'Editor XML. Le proprietà disponibili variano in base al tipo di documento XML correntemente attivo.

> [!NOTE]
> Tutte le proprietà del documento XML vengono salvate nella soluzione. Di conseguenza, non sarà necessario immettere nuovamente tali valori alla successiva apertura della soluzione.

 **Codifica**

 La codifica dei caratteri per il file. Modificando questa proprietà si modifica anche l'attributo della codifica nella dichiarazione XML e viceversa. La nuova codifica verrà usata per codificare il file quando viene salvato.

 **Input**

 Il documento di input associato al foglio di stile XSLT. Viene usato per il **ShowXSLT Output** comando. Un documento può essere selezionato utilizzando il pulsante Sfoglia (**...** ) pulsante.

 Questa proprietà è visibile solo quando il file XSLT è correntemente attivo nella finestra dell'editor.

 **Output**

 Il file che viene generato durante la trasformazione di un documento XML.

 Se un file non è specificato, verrà generato un nome file predefinito in base all'attributo `method` dell'elemento `xsl:output` che determina l'estensione del file. Il file predefinito si trova nella directory temporanea dell'utente corrente.

 **Schemi**

 Gli schemi da usare per la convalida. Il pulsante apre il **schemi XSD** nella finestra di dialogo può essere usata per selezionare gli schemi da usare.

 È possibile anche immettere il percorso degli schemi. Se vengono specificati più schemi, ogni singolo percorso di schema deve essere racchiuso tra virgolette.

 **Foglio di stile**

 Il file XSLT utilizzato per trasformare il documento quando la **Mostra l'Output XSLT** comando viene utilizzato. Se questo campo è vuoto quando il **Mostra l'Output XSLT** comando viene utilizzato, l'editor utilizzerà il valore fornito nel `xml-stylesheet` istruzione del documento o di elaborazione richiede il nome del file.

 Quando si modifica un file XSLT, questa proprietà può essere utilizzata per specificare che deve essere un foglio di stile utilizzato quando la **Mostra l'Output XSLT** o **Debug XSLT** comando selezionato. Ad esempio, è possibile eseguire tale operazione quando si modifica un foglio di stile incluso in un foglio di stile padre.

## <a name="see-also"></a>Vedere anche

- [Editor XML](../xml-tools/xml-editor.md)
- [Componenti dell'Editor XML](../xml-tools/xml-editor-components.md)