---
title: Localizzazione dei comandi di menu Documenti Microsoft
ms.date: 10/08/2019
ms.topic: conceptual
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d363b495eb84dc3bfeabd7bf7c5d05fabcbc4d36
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702952"
---
# <a name="localize-menu-commands"></a>Localizzare i comandi di menu

È possibile fornire testo localizzato per i comandi di menu e barra degli strumenti creando file *vsct* localizzati e file *resx localizzati* per il pacchetto VSPackage e quindi aggiornando i file di progetto per incorporare le modifiche.

Per informazioni su come localizzare l'esperienza di installazione, vedere [Localizzare pacchetti VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="localize-command-names"></a>Localizzare i nomi dei comandi

In VSPackage, i comandi di menu e i pulsanti della barra degli strumenti sono definiti nel file *vsct.*

1. In **Esplora soluzioni**modificare il nome del file *vsct* da *filename.vsct* a *filename.en-US.vsct*.

2. Creare una copia di *filename.en-US.vsct* per ogni lingua localizzata.

    Assegna un nome a ogni nome file di *copia. Locale, vsct*, dove *"Locale"* è un nome di impostazioni cultura specifico. Per un elenco dei valori dei nomi delle impostazioni cultura, vedere [ID delle impostazioni locali assegnati da Microsoft](/windows/uwp/publish/supported-languages).

    Questi *nomi di file. I file Locale.vsct* conterranno il testo del menu localizzato per il pacchetto.

3. Aprire ogni *nome di file. Locale.vsct* per localizzare il testo.

   1. Modificare i valori dell'elemento [ButtonText](../extensibility/buttontext-element.md) in base alla lingua specifica.

   2. Se si forniscono icone localizzate, modificare i valori [Bitmap](../extensibility/bitmap-element.md) in modo che puntino ai file di destinazione.

      L'esempio seguente mostra il testo del pulsante inglese e spagnolo per un comando per aprire una finestra degli strumenti di Family Tree Explorer.

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

## <a name="localize-other-text-resources"></a>Localizzare altre risorse di testoLocalize other text resources

Le risorse di testo diverse dai nomi dei comandi sono definite nei file di risorse (*RESX*).

1. Rinominare *VSPackage.resx* in *VSPackage.en-US.resx*.

2. Creare una copia del file *VSPackage.en-US.resx* per ogni lingua localizzata.

     Denominare ogni copia *VSPackage. Locale, resx*, dove *"Locale"* è un nome di impostazioni cultura specifico.

3. Rinominare *Resources.resx* in *Resources.en-US.resx*.

4. Creare una copia del file *Resources.en-US.resx* per ogni lingua localizzata.

     Denominare ogni copia *Risorse. Locale, resx*, dove *"Locale"* è un nome di impostazioni cultura specifico.

5. Aprire ogni file *con estensione resx* per modificare i valori stringa in base alla lingua e alle impostazioni cultura specifiche. Nell'esempio seguente viene illustrata la definizione di risorsa localizzata per la barra del titolo di una finestra degli strumenti.

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

## <a name="incorporate-localized-resources-into-the-project"></a>Incorporare risorse localizzate nel progetto

È necessario modificare il file *di assemblyinfo.cs* e il file di progetto per incorporare le risorse localizzate.

1. Dal nodo **Proprietà** in **Esplora soluzioni**aprire *assemblyinfo.cs* o *assemblyinfo.vb* nell'editor.

2. Aggiungere la seguente voce.

    ```csharp
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]
    ```

     In questo modo viene impostata l'inglese americano come lingua predefinita.

3. Scaricare il progetto.

4. Aprire il file di progetto nell'editor.

5. Nell'elemento `Project` radice aggiungere `PropertyGroup` un `UICulture` elemento con un elemento che corrisponda alla lingua predefinita.

    ```xml
    <PropertyGroup>
      <UICulture>en-US</UICulture>
    </PropertyGroup>
    ```

     In questo modo viene impostato l'inglese degli Stati Uniti come impostazioni cultura predefinite dell'interfaccia utente per i controlli Windows Presentation Foundation (WPF).

6. Individuare `ItemGroup` l'elemento `EmbeddedResource` che contiene elementi.

7. Nell'elemento `EmbeddedResource` che chiama *VSPackage.en-US.resx*, sostituire l'elemento `ManifestResourceName` con un `LogicalName` elemento impostato su `VSPackage.en-US.Resources`, come segue:

    ```xml
    <EmbeddedResource Include="VSPackage.en-US.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <LogicalName>VSPackage.en-US.Resources</LogicalName>
    </EmbeddedResource>
    ```

8. Per ogni lingua localizzata, copiare `EmbeddedResource` l'elemento `VsPackage.en-US`per e impostare l'attributo **Include** e l'elemento **LogicalName** della copia nelle impostazioni locali di destinazione.

9. Per ogni `VSCTCompile` elemento localizzato, aggiungere un `ResourceName` elemento che punti a `Menus.ctmenu`, come illustrato nell'esempio seguente:

    ```xml
    <ItemGroup>
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>
    ```

10. Salvare il file di progetto e ricaricare il progetto.

11. Compilare il progetto.

     In questo modo vengono creati un assembly principale e assembly di risorse per ogni lingua. Per informazioni sulla localizzazione del processo di distribuzione, vedere [Localizzare pacchetti VSIXFor](../extensibility/localizing-vsix-packages.md) information on localizing the deployment process, see Localize VSIX packages

## <a name="see-also"></a>Vedere anche

- [Estendere menu e comandi](../extensibility/extending-menus-and-commands.md)
- [Globalizzare e localizzare le applicazioni](../ide/globalizing-and-localizing-applications.md)
