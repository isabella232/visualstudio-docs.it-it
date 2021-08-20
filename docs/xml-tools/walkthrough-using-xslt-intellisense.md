---
title: 'Procedura dettagliata: utilizzo di XSLT IntelliSense'
description: Informazioni su come usare XSLT IntelliSense per completare automaticamente i valori di alcuni attributi seguendo i passaggi di questa procedura dettagliata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 079d95ac-2eaf-4ae1-9cd3-2c81a961a942
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: d13c949746e9bad5d926862ae3870f8b1d52980e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122122592"
---
# <a name="walkthrough-using-xslt-intellisense"></a>Procedura dettagliata: utilizzo di XSLT IntelliSense

Questa procedura dettagliata dimostra come usare XSLT IntelliSense per completare automaticamente il valore di alcuni attributi.

## <a name="to-use-intellisense-in-the-name-attribute-of-xslwith-param-and-xslcall-template-elements"></a>Per usare IntelliSense nell'attributo del nome degli elementi xsl:with-param e xsl:call-template

1. Creare un nuovo file XSLT e copiarvi il seguente codice:

    ```xml
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
    <!-- These 2 elements effectively assign
         $messages = resources/en.xml/<messages>,
         then $messages is used in the "localized-message" template.  -->
    <xsl:param name="lang">en</xsl:param>
    <xsl:variable name="messages"
          select="document(concat('resources/', $lang, '.xml'))/messages"/>

    <xsl:template name="msg23" match="msg23">
    </xsl:template>

    <xsl:template name="localized-message">
      <xsl:param name="msgcode"/>
      <!-- Show message string. -->
      <xsl:message terminate="yes">
        <xsl:value-of select="$messages/message[@name=$msgcode]"/>
      </xsl:message>
    </xsl:template>
    </xsl:stylesheet>
    ```

2. Inserire il cursore `<xsl:template name="msg23" match="msg23">` dopo e premere **INVIO.** Quindi iniziare a digitare il seguente elemento `xsl:call-template`:

    ```xml
    <xsl:call-template name="localized-message">
    </xsl:call-template>
    ```

     L'elenco dei nomi di modello viene visualizzato nell'attributo `name=""` dell'elemento `xsl:call-template` durante la digitazione.

3. Inserire il cursore `<xsl:call-template name="localized-message">` dopo e premere **INVIO.** Quindi iniziare a digitare il seguente elemento `xsl:with-param`:

    ```xml
    <xsl:with-param name="msgcode">msg23</xsl:with-param>
    ```

     L'elenco dei nomi di parametro viene visualizzato nell'attributo `name=""` dell'elemento `xsl:with-param`.

## <a name="to-use-intellisense-in-the-mode-attribute-of-an-xslapply-templates-element"></a>Per usare IntelliSense nell'attributo mode di un elemento xsl:apply-templates

1. Creare un nuovo file XSLT e copiarvi il seguente codice:

    ```xml
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
      <xsl:template match="/">
        <HTML>
          <BODY>
            <TABLE>
              <xsl:apply-templates select="customers/customer">
                <xsl:sort select="state"/>
                <xsl:sort select="name"/>
              </xsl:apply-templates>
            </TABLE>
          </BODY>
        </HTML>
      </xsl:template>
      <xsl:template match="customer">
        <TR>
          <xsl:apply-templates select="name" />
          <xsl:apply-templates select="address" />
          <xsl:apply-templates select="phone" />
        </TR>
      </xsl:template>
      <xsl:template match="name">
        <TD STYLE="font-size:14pt font-family:serif">
          <xsl:apply-templates />
        </TD>
      </xsl:template>
      <xsl:template match="address">
        <TD>
          <xsl:apply-templates />
        </TD>
      </xsl:template>
      <xsl:template match="phone">
        <TD>
          <xsl:apply-templates />
        </TD>
      </xsl:template>
      <xsl:template match="phone" mode="accountNumber">
        <xsl:param name="Area_Code"/>
        <TD STYLE="font-style:italic">
          1-<xsl:value-of select="."/>-001
        </TD>
      </xsl:template>
    </xsl:stylesheet>
    ```

2. Inserire il cursore `<xsl:apply-templates select="phone" />` dopo e premere **INVIO.** Quindi iniziare a digitare il seguente elemento `xsl: apply-templates`:

    ```xml
    <xsl:apply-templates select="phone"  mode="accountNumber">
    ```

     L'elenco delle modalità modello viene visualizzato nell'attributo `mode=""` dell'elemento `xsl:apply-templates`.

## <a name="to-use-intellisense-in-the-stylesheet-prefix-and-result-prefix-attributes-of-an-xslnamespace-alias-element"></a>Per usare IntelliSense negli attributi stylesheet-prefix e result-prefix di un elemento xsl:namespace-alias

1. Creare un nuovo file XSLT e copiarvi il seguente codice:

    ```xml
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:alt="http://www.w3.org/1999/XSL/Transform-alternate"
    version="1.0">
      <xsl:param name="browser" select="'InternetExplorer'"/>
      <xsl:template match="/">
        <alt:stylesheet>
          <xsl:choose>
            <xsl:when test="$browser='InternetExplorer'">
              <alt:import href="IERoutines.xsl"/>
              <alt:template match="/">
                <div>
                  <alt:call-template name="showTable"/>
                </div>
              </alt:template>
            </xsl:when>
            <xsl:otherwise>
              <alt:import href="OtherBrowserRoutines.xsl"/>
              <alt:template match="/">
                <div>
                  <alt:call-template name="showTable"/>
                </div>
              </alt:template>
            </xsl:otherwise>
          </xsl:choose>
        </alt:stylesheet>
      </xsl:template>
    </xsl:stylesheet>
    ```

2. Inserire il cursore `<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:alt="http://www.w3.org/1999/XSL/Transform-alternate" version="1.0">` dopo e premere **INVIO.** Quindi iniziare a digitare il seguente elemento `xsl:namespace-alias`:

    ```xml
    <xsl:namespace-alias stylesheet-prefix="alt" result-prefix="xsl"/>
    ```

     Notare come l'elenco dei prefissi viene visualizzato negli attributi `stylesheet-prefix` e `result-prefix` dell'elemento `xsl:namespace-alias`.

## <a name="see-also"></a>Vedi anche

- [Funzionalità IntelliSense dell'editor XML](../xml-tools/xml-editor-intellisense-features.md)
