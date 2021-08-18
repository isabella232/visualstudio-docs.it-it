---
title: Proprietà dei documenti XML, finestra Proprietà
description: Informazioni sulle proprietà del documento XML nel Finestra Proprietà che forniscono informazioni di base sul documento attivo nell'editor XML.
ms.custom: SEO-VS-2020
ms.date: 03/05/2019
ms.topic: reference
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: 3e68945d5cd58384a5ccba64bff458be51ba748d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135039"
---
# <a name="xml-document-properties-properties-window"></a>Proprietà del documento XML, Finestra Proprietà

La **finestra** Proprietà fornisce informazioni di base sul documento attivo nell'editor XML. Le proprietà disponibili variano in base al tipo di documento XML correntemente attivo.

> [!NOTE]
> Tutte le proprietà del documento XML vengono salvate nella soluzione. Di conseguenza, non sarà necessario immettere nuovamente tali valori alla successiva apertura della soluzione.

**Encoding**

La codifica dei caratteri per il file. Modificando questa proprietà si modifica anche l'attributo della codifica nella dichiarazione XML e viceversa. La nuova codifica viene usata per codificare il file quando si salva il file.

**Input**

Il documento di input associato al foglio di stile XSLT. Viene usato dai comandi **XSLT Start,** ad esempio **XML**  >  **Start XSLT Without Debugging**. È possibile selezionare un documento usando il pulsante Sfoglia (**...**).

Questa proprietà è visibile solo quando un file XSLT è aperto nell'editor.

**Output**

Il file che viene generato durante la trasformazione di un documento XML.

Se non viene specificato un file, viene generato un nome file predefinito in base all'attributo dell'elemento `method` `xsl:output` , che determina l'estensione del file. Il file predefinito si trova nella directory temporanea dell'utente corrente.

**Schemi**

Gli schemi da usare per la convalida. Il pulsante apre la finestra di dialogo Schemi **XSD,** che può essere usata per selezionare gli schemi da usare.

È possibile anche immettere il percorso degli schemi. Se vengono specificati più schemi, ogni singolo percorso di schema deve essere racchiuso tra virgolette.

**Stylesheet**

File XSLT utilizzato per trasformare il documento quando vengono usati i comandi Avvia debug **XSLT** e Avvia **XSLT senza** debug. Se questo campo è vuoto, l'editor usa il valore fornito nell'istruzione di elaborazione del documento oppure richiede `xml-stylesheet` un nome file.

Quando si modifica un file XSLT, questa proprietà può essere utilizzata per specificare che deve essere usato un foglio di stile diverso quando si seleziona il comando Avvia debug **XSLT** o Avvia **XSLT** senza debug. Ad esempio, è possibile eseguire questa operazione quando si modifica un foglio di stile incluso in un foglio di stile padre.

## <a name="see-also"></a>Vedi anche

- [Editor XML](../xml-tools/xml-editor.md)
