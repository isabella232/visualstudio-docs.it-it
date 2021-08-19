---
title: Cache dello schema dell'editor XML
description: Informazioni sulla cache dello schema fornita dall'editor XML che include schemi XML standard usati per IntelliSense e la convalida di documenti XML.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 35a7fcad-f3bf-4a96-9008-4306e7276223
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: 213ba44d2a2f7ae24a00ea3d103bc7d04d775616
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122098671"
---
# <a name="schema-cache"></a>Cache dello schema

L'editor XML fornisce una cache dello schema che si trova nella directory *%VSInstallDir%\xml\Schemas.* La cache dello schema è globale per tutti gli utenti del computer e include schemi XML standard usati per IntelliSense e la convalida di documenti XML.

L'editor XML può anche trovare gli schemi presenti nella soluzione, gli  schemi specificati nel campo **Schemi** della finestra Proprietà del documento e gli schemi identificati dagli `xsi:schemaLocation` attributi e `xsi:noNamespaceSchemaLocation` .

Nella tabella seguente vengono descritti gli schemi installati con l'editor XML.

| Nome file | Descrizione |
|-| - |
| *catalog.xsd* | Schema per i file del catalogo schemi dell'editor XML. Per informazioni sui cataloghi degli schemi, vedere di seguito. |
| *DotNetConfig.xsd* | Schema per Web.Config file, `http://schemas.microsoft.com/.NETConfiguration/v2.0` . |
| *msbuild.xsd* | Schema per l'MSBuild creare file, `http://schemas.microsoft.com/developer/msbuild/2003` . |
| *msdata.xsd* | Schema per le annotazioni XSD aggiunte dalla classe <xref:System.Data.DataSet>, "urn:schemas-microsoft-com:xml-msdata". |
| *msxsl.xsd* | Schema per le estensioni del blocco di script Microsoft XSLT, urn:schemas-microsoft-com:xslt. |
| *SnippetFormat.xsd* | Schema per i file XML del frammento di codice. Per esempi, vedere *%VSInstallDir%\VC#\Expansions.* |
| *Soap1.1.xsd* | Schema per Simple Object Access Protocol (SOAP) 1.1, `http://schemas.xmlsoap.org/soap/envelope/` . |
| *Soap1.2.xsd* | Schema per il protocollo SOAP (Simple Object Access Protocol) 1.2. |
| *SiteMapSchema.xsd* | Schema per ASP.NET file XML della mappa del sito, `http://schemas.microsoft.com/AspNet/SiteMap-File-1.0` . |
| *wsdl.xsd* | Schema per il linguaggio di descrizione del servizio Web, `http://schemas.xmlsoap.org/wsdl/` . |
| *xenc.xsd* | Schema per la crittografia XML, `http://www.w3.org/2000/09/xmldsig#` . |
| *xhtml.xsd* | Schema per XHTML `http://www.w3.org/1999/xhtml` . |
| *xlink.xsd* | Schema per XLink1.0, `http://www.w3.org/1999/xlink` . |
| *xml.xsd* | Schema che descrive gli attributi xml:space e xml:lang, `http://www.w3.org/XML/1998/namespace` . |
| *xmlsig.xsd* | Schema per le firme digitali XML, `http://www.w3.org/2000/09/xmldsig#` . |
| *xsdschema.xsd* | Schema che descrive XSD stesso, `http://www.w3.org/2001/XMLSchema` . |
| *xslt.xsd* | Schema per le trasformazioni XML, `http://www.w3.org/1999/XSL/Transform` . |

## <a name="update-schemas-in-the-cache"></a>Aggiornare gli schemi nella cache

L'editor carica la directory della cache di schema quando il package editor XML viene caricato e verifica le eventuali modifiche durante l'esecuzione. Se è stato aggiunto uno schema, esso viene caricato automaticamente in un indice di schemi noti in memoria. Se è stato rimosso uno schema, esso viene automaticamente rimosso dall'indice in memoria. Se è stato aggiornato uno schema, esso invalida automaticamente la cache degli schemi in memoria.

> [!NOTE]
> Poiché la directory della cache di schema è globale, è sufficiente aggiungere qui gli schemi standard utili per tutti i progetti di Visual Studio che è possibile creare sul proprio computer.

L'editor XML supporta inoltre un numero illimitato di file del catalogo degli schemi nella directory della cache. Per i cataloghi degli schemi è possibile scegliere altre posizioni per gli schemi che si desidera tenere sempre ben presenti nell'editor. Il file *catalog.xsd* definisce il formato per il file di catalogo ed è incluso nella directory della cache dello schema. Il *catalog.xml* è il catalogo predefinito e contiene collegamenti ad altri schemi in *%VSInstallDir%*. Di seguito è riportato un campionamento del file *catalog.xml:*

```xml
<SchemaCatalog xmlns="http://schemas.microsoft.com/xsd/catalog">
  <Schema href="%VSInstallDir%/help/schemas/Favorites.xsd" targetNamespace="urn:Favorites-Schema"/>
  <Schema href="%VSInstallDir%/help/schemas/Links.xsd" targetNamespace="urn:Links-Schema"/>
  <Schema href="%VSInstallDir%/help/schemas/MyHelp.xsd" targetNamespace="urn:VSHelp-Schema"/>
</SchemaCatalog>
```

L'attributo `href` può essere un qualsiasi percorso di file o URL di tipo http che fa riferimento allo schema. Il percorso del file può essere relativo al documento catalogo. Le variabili seguenti, delimitate da %%, vengono riconosciute dall'editor ed espanse nel percorso:

- VSInstallDir

- Sistema

- ProgramFiles

- Programmi

- CommonProgramFiles

- ApplicationData

- CommonApplicationData

- LCID

Nel documento catalogo può essere incluso un elemento `Catalog` che fa riferimento ad altri cataloghi. È possibile usare l'elemento `Catalog` per scegliere un catalogo centrale condiviso dal team o dalla società o un catalogo online condiviso con i partner commerciali. L'attributo `href` è il percorso del file o l'URL di tipo http per gli altri cataloghi. Di seguito è riportato un esempio dell'elemento `Catalog`:

```xml
<Catalog href="file://c:/xcbl/xcblCatalog.xml"/>
```

Con il catalogo è inoltre possibile controllare in che modo gli schemi vengono associati ai documenti XML usando l'elemento speciale `Association`. Questo elemento associa schemi senza spazio dei nomi di destinazione a una determinata estensione di file, che può essere utile perché l'editor XML non esegue alcuna associazione automatica di schemi che non dispongono di un `targetNamespace` attributo . Nell'esempio seguente l'elemento `Association` associa lo schema dotNetConfig con tutti i file che presentano l'estensione "config":

```xml
<Association extension="config" schema="%VSInstallDir%/xml/schemas/dotNetConfig.xsd"/>
```

## <a name="localized-schemas"></a>Schemi localizzati

In molti casi il *catalog.xml* file non contiene voci per gli schemi localizzati. È possibile aggiungere altre voci al file *catalog.xml* che puntano alla directory dello schema localizzato.

Nell'esempio seguente è stato creato un nuovo elemento `Schema` che usa la variabile % LCID% per fare riferimento allo schema localizzato.

```xml
<Schema href="%InstallRoot%/Common7/IDE/Policy/Schemas/%LCID%/TDLSchema.xsd"
  targetNamespace="http://www.microsoft.com/schema/EnterpriseTemplates/TDLSchema"/>
```

## <a name="change-the-location-of-the-schema-cache"></a>Modificare il percorso della cache dello schema

È possibile personalizzare il percorso per la cache dello schema usando la **pagina Opzioni** varie. Se si dispone di una directory di schemi preferiti, è possibile configurare l'editor in modo da usare solo questi schemi.

> [!NOTE]
> Tale modifica ha effetto solo sull'utente corrente di Visual Studio.

### <a name="to-change-the-schema-cache-location"></a>Per modificare il percorso della cache degli schemi

1. Scegliere **Opzioni** dal menu **Strumenti**.

2. Espandere **Editor di testo**, **XML** e quindi fare clic su **Varie**.

3. Fare clic **sul pulsante** Sfoglia nel **campo** Schemi.

4. Selezionare la cartella per la cache dello schema e fare clic su **OK.**

### <a name="to-add-another-directory-of-common-schemas"></a>Per aggiungere un'altra directory di schemi comuni

1. Modificare il *catalog.xml* file nella directory della cache dello schema dell'editor XML.

2. Aggiungere un nuovo elemento `<Catalog href="..."/>` che fa riferimento alla directory degli schemi aggiuntivi.

3. Salvare le modifiche.

   Il catalogo viene ricaricato automaticamente.

## <a name="see-also"></a>Vedi anche

- [Editor XML](../xml-tools/xml-editor.md)
