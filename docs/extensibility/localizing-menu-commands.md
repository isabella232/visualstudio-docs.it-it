---
title: Localizzazione di comandi di Menu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd5755f2b0bf8fe4379d503d952341f176c0b870
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56679268"
---
# <a name="localize-menu-commands"></a>Localizzare i comandi di menu
È possibile fornire il testo localizzato per i comandi di menu e barra degli strumenti mediante la creazione di localizzata *vsct* i file e localizzate *resx* file per il pacchetto VSPackage e quindi aggiornare i file di progetto incorporare il modifiche.

 Per informazioni su come localizzare l'esperienza di installazione, vedere [pacchetti VSIX localizzare](../extensibility/localizing-vsix-packages.md).

## <a name="localize-command-names"></a>Localizzare i nomi dei comandi
 Nei pacchetti VSPackage, i comandi di menu e pulsanti della barra degli strumenti sono definiti nel *vsct* file.

1. In **Esplora soluzioni**, modificare il nome del *con estensione vsct* del file da *filename.vsct* a *filename.en US.vsct*.

2. Creare una copia del *filename.en US.vsct* per ogni lingua localizzata.

    Nome di ogni copia *filename. { Impostazioni locali} vsct*, dove *{delle impostazioni locali}* è un nome di impostazioni cultura particolari. Per un elenco di valori di nome impostazioni cultura, vedere [ID impostazioni locali assegnati da Microsoft](/windows/uwp/publish/supported-languages).

    Questi *filename. Locale.vsct* file conterrà il testo del menu localizzato per il pacchetto.

3. Aprire ogni *filename. Locale.vsct* file per localizzare il testo.

   1. Modificare il [ButtonText](../extensibility/buttontext-element.md) elemento i valori come appropriato per la lingua particolare.

   2. Se si intende fornire le icone localizzate, modificare il [Bitmap](../extensibility/bitmap-element.md) valori in modo che punti ai file di destinazione.

      L'esempio seguente illustra l'inglese e spagnolo testo del pulsante aprire una finestra degli strumenti dell'albero genealogico Esplora un comando.

      [*FamilyTree.en-US.vsct*]

   ```xml
   <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
     <Icon guid="guidImages" id="bmpPic2" />
     <Strings>
       <CommandName>cmdidFamilyTree</CommandName>
       <ButtonText>Family Tree Explorer</ButtonText>
     </Strings>
   </Button>
   ```

    [*FamilyTree.es-ES.vsct*]

   ```xml
   <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
     <Icon guid="guidImages" id="bmpPic2" />
     <Strings>
       <CommandName>cmdidFamilyTree</CommandName>
       <ButtonText>Explorar el arbol genealogico</ButtonText>
     </Strings>
   </Button>

   ```

## <a name="localize-other-text-resources"></a>Localizzare le altre risorse di testo
 Le risorse di testo diverso da nomi di comando vengono definite nella risorsa (*resx*) file.

1.  Rinominare *VSPackage.resx* al *VSPackage.en-us. resx*.

2.  Creare una copia del *VSPackage.en-us. resx* file per ogni lingua localizzata.

     Nome di ogni copia *VSPackage. { Impostazioni locali} resx*, dove *{delle impostazioni locali}* è un nome di impostazioni cultura particolari.

3.  Rinominare *Resources. resx* al *Resources. en-us. resx*.

4.  Creare una copia del *Resources. en-us. resx* file per ogni lingua localizzata.

     Nome di ogni copia *le risorse. { Impostazioni locali} resx*, dove *{delle impostazioni locali}* è un nome di impostazioni cultura particolari.

5.  Aprire ognuno *resx* file per modificare la stringa di valori come appropriato per la lingua particolare. Nell'esempio seguente illustra la definizione di risorsa localizzata per la barra del titolo di una finestra degli strumenti.

     [*Resources.en-US.resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Family Tree Explorer</value>
    </data>
    ```

     [*Resources.es-ES.resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Explorador del arbol genealogico</value>
    </data>

    ```

## <a name="incorporate-localized-resources-into-the-project"></a>Incorporare le risorse localizzate nel progetto
 È necessario modificare il *assemblyinfo.cs* file e il file di progetto per incorporare le risorse localizzate.

1.  Dal **delle proprietà** nodo nel **Esplora soluzioni**, aprire *assemblyinfo.cs* o *AssemblyInfo. vb* nell'editor.

2.  Aggiungere la voce seguente.

    ```csharp
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]
    ```

     Consente di impostare inglese come lingua predefinita.

3.  Scaricare il progetto.

4.  Aprire il file di progetto nell'editor.

5.  Individuare il `ItemGroup` elemento contenente `EmbeddedResource` elementi.

6.  Nel `EmbeddedResource` elemento che chiama *VSPackage.en-us. resx*, sostituire il `ManifestResourceName` elemento con un `LogicalName` elemento, impostato su `VSPackage.en-US.Resources`, come indicato di seguito.

    ```xml
    <EmbeddedResource Include="VSPackage.en-US.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <LogicalName>VSPackage.en-US.Resources</LogicalName>
    </EmbeddedResource>
    ```

7.  Per ogni lingua localizzata, copiare il `EmbeddedResource` (elemento) per `VsPackage.en-US`e impostare le **inclusione** attributo e **LogicalName** elemento della copia in impostazioni locali di destinazione, come illustrato di seguito esempio.

8.  A ogni localizzato `VSCTCompile` elemento, aggiungere un' `ResourceName` elemento al quale punta `Menus.ctmenu`, come illustrato nell'esempio seguente.

    ```xml
    <ItemGroup>
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>
    ```

9. Salvare il file di progetto e ricaricare il progetto.

10. Compilare il progetto.

     Verrà creato un assembly principale e gli assembly di risorse per ogni lingua. Per informazioni sulla localizzazione il processo di distribuzione, vedere [pacchetti VSIX localizzare](../extensibility/localizing-vsix-packages.md)

## <a name="see-also"></a>Vedere anche
- [Estendere i menu e comandi](../extensibility/extending-menus-and-commands.md)
- [Confronto tra oggetti MenuCommand Visual Studio. OleMenuCommands](../extensibility/menucommands-vs-olemenucommands.md)
- [Globalizzare e localizzare le applicazioni](../ide/globalizing-and-localizing-applications.md)