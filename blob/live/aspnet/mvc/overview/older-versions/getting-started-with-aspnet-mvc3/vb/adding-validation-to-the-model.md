---
uid: mvc/overview/older-versions/getting-started-with-aspnet-mvc3/vb/adding-validation-to-the-model
title: "Adicionando validação para o modelo (VB) | Microsoft Docs"
author: Rick-Anderson
description: "Este tutorial ensina as Noções básicas de criação de um aplicativo Web do ASP.NET MVC usando o Microsoft Visual Web Developer 2010 Express Service Pack 1, que é..."
ms.author: aspnetcontent
manager: wpickett
ms.date: 01/12/2011
ms.topic: article
ms.assetid: 878f6c31-972d-45f4-8849-5c633b511409
ms.technology: dotnet-mvc
ms.prod: .net-framework
msc.legacyurl: /mvc/overview/older-versions/getting-started-with-aspnet-mvc3/vb/adding-validation-to-the-model
msc.type: authoredcontent
ms.openlocfilehash: d36ce4e2735bdc73e8731eae27346edec47998cf
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2017
---
<a name="adding-validation-to-the-model-vb"></a><span data-ttu-id="5b1dc-103">Adicionando validação para o modelo (VB)</span><span class="sxs-lookup"><span data-stu-id="5b1dc-103">Adding Validation to the Model (VB)</span></span>
====================
<span data-ttu-id="5b1dc-104">Por [Rick Anderson](https://github.com/Rick-Anderson)</span><span class="sxs-lookup"><span data-stu-id="5b1dc-104">by [Rick Anderson](https://github.com/Rick-Anderson)</span></span>

> <span data-ttu-id="5b1dc-105">Este tutorial ensina as Noções básicas de criação de um aplicativo Web do ASP.NET MVC usando o Microsoft Visual Web Developer 2010 Express Service Pack 1, que é uma versão gratuita do Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-105">This tutorial will teach you the basics of building an ASP.NET MVC Web application using Microsoft Visual Web Developer 2010 Express Service Pack 1, which is a free version of Microsoft Visual Studio.</span></span> <span data-ttu-id="5b1dc-106">Antes de começar, verifique se que você instalou os pré-requisitos listados abaixo.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-106">Before you start, make sure you've installed the prerequisites listed below.</span></span> <span data-ttu-id="5b1dc-107">Você pode instalar todos eles clicando no link a seguir: [Web Platform Installer](https://www.microsoft.com/web/gallery/install.aspx?appid=VWD2010SP1Pack).</span><span class="sxs-lookup"><span data-stu-id="5b1dc-107">You can install all of them by clicking the following link: [Web Platform Installer](https://www.microsoft.com/web/gallery/install.aspx?appid=VWD2010SP1Pack).</span></span> <span data-ttu-id="5b1dc-108">Como alternativa, você pode instalar individualmente os pré-requisitos usando os links a seguir:</span><span class="sxs-lookup"><span data-stu-id="5b1dc-108">Alternatively, you can individually install the prerequisites using the following links:</span></span>
> 
> - [<span data-ttu-id="5b1dc-109">Pré-requisitos de Visual Studio Web Developer Express SP1</span><span class="sxs-lookup"><span data-stu-id="5b1dc-109">Visual Studio Web Developer Express SP1 prerequisites</span></span>](https://www.microsoft.com/web/gallery/install.aspx?appid=VWD2010SP1Pack)
> - [<span data-ttu-id="5b1dc-110">Atualização de ferramentas do ASP.NET MVC 3</span><span class="sxs-lookup"><span data-stu-id="5b1dc-110">ASP.NET MVC 3 Tools Update</span></span>](https://www.microsoft.com/web/gallery/install.aspx?appsxml=&amp;appid=MVC3)
> - <span data-ttu-id="5b1dc-111">[SQL Server Compact 4.0](https://www.microsoft.com/web/gallery/install.aspx?appid=SQLCE;SQLCEVSTools_4_0)(tempo de execução + ferramentas de suportam)</span><span class="sxs-lookup"><span data-stu-id="5b1dc-111">[SQL Server Compact 4.0](https://www.microsoft.com/web/gallery/install.aspx?appid=SQLCE;SQLCEVSTools_4_0)(runtime + tools support)</span></span>
> 
> <span data-ttu-id="5b1dc-112">Se você estiver usando o Visual Studio 2010 em vez do Visual Web Developer 2010, instale os pré-requisitos clicando no link a seguir: [pré-requisitos do Visual Studio 2010](https://www.microsoft.com/web/gallery/install.aspx?appsxml=&amp;appid=VS2010SP1Pack).</span><span class="sxs-lookup"><span data-stu-id="5b1dc-112">If you're using Visual Studio 2010 instead of Visual Web Developer 2010, install the prerequisites by clicking the following link: [Visual Studio 2010 prerequisites](https://www.microsoft.com/web/gallery/install.aspx?appsxml=&amp;appid=VS2010SP1Pack).</span></span>
> 
> <span data-ttu-id="5b1dc-113">Um projeto do Visual Web Developer com VB.NET código-fonte está disponível para acompanhar este tópico.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-113">A Visual Web Developer project with VB.NET source code is available to accompany this topic.</span></span> <span data-ttu-id="5b1dc-114">[Baixe a versão VB.NET](https://code.msdn.microsoft.com/Introduction-to-MVC-3-10d1b098).</span><span class="sxs-lookup"><span data-stu-id="5b1dc-114">[Download the VB.NET version](https://code.msdn.microsoft.com/Introduction-to-MVC-3-10d1b098).</span></span> <span data-ttu-id="5b1dc-115">Se você preferir c#, alterne para o [versão c#](../cs/adding-validation-to-the-model.md) deste tutorial.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-115">If you prefer C#, switch to the [C# version](../cs/adding-validation-to-the-model.md) of this tutorial.</span></span>


<span data-ttu-id="5b1dc-116">Nesta seção, você adicionará a lógica de validação de `Movie` modelo e você garantirá que as regras de validação são aplicadas a qualquer momento em que um usuário tenta criar ou editar um filme usando o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-116">In this section you'll add validation logic to the `Movie` model, and you'll ensure that the validation rules are enforced any time a user attempts to create or edit a movie using the application.</span></span>

## <a name="keeping-things-dry"></a><span data-ttu-id="5b1dc-117">Manter as coisas SECA</span><span class="sxs-lookup"><span data-stu-id="5b1dc-117">Keeping Things DRY</span></span>

<span data-ttu-id="5b1dc-118">Um dos fundamentos de design do ASP.NET MVC é simulação ("não repetitivo").</span><span class="sxs-lookup"><span data-stu-id="5b1dc-118">One of the core design tenets of ASP.NET MVC is DRY ("Don't Repeat Yourself").</span></span> <span data-ttu-id="5b1dc-119">ASP.NET MVC incentiva você a especificar funcionalidade ou comportamento somente uma vez e, em seguida, ter refletidas em qualquer lugar em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-119">ASP.NET MVC encourages you to specify functionality or behavior only once, and then have it be reflected everywhere in an application.</span></span> <span data-ttu-id="5b1dc-120">Isso reduz a quantidade de código que você precisa para escrever e faz com que o código que você escreve muito mais fácil para manter.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-120">This reduces the amount of code you need to write and makes the code you do write much easier to maintain.</span></span>

<span data-ttu-id="5b1dc-121">O suporte de validação fornecido pelo ASP.NET MVC e o Entity Framework Code First é um ótimo exemplo do princípio seco em ação.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-121">The validation support provided by ASP.NET MVC and Entity Framework Code First is a great example of the DRY principle in action.</span></span> <span data-ttu-id="5b1dc-122">Você pode especificar declarativamente regras de validação em um lugar (a classe de modelo) e, em seguida, essas regras serão impostas em qualquer lugar no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-122">You can declaratively specify validation rules in one place (in the model class) and then those rules are enforced everywhere in the application.</span></span>

<span data-ttu-id="5b1dc-123">Vamos ver como você pode tirar proveito desse suporte de validação no aplicativo de filme.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-123">Let's look at how you can take advantage of this validation support in the movie application.</span></span>

## <a name="adding-validation-rules-to-the-movie-model"></a><span data-ttu-id="5b1dc-124">Adicionando regras de validação para o modelo de filme</span><span class="sxs-lookup"><span data-stu-id="5b1dc-124">Adding Validation Rules to the Movie Model</span></span>

<span data-ttu-id="5b1dc-125">Você começará com a adição de alguma lógica de validação para o `Movie` classe.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-125">You'll begin by adding some validation logic to the `Movie` class.</span></span>

<span data-ttu-id="5b1dc-126">Abra o *Movie.vb* arquivo.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-126">Open the *Movie.vb* file.</span></span> <span data-ttu-id="5b1dc-127">Adicionar um `Imports` instrução na parte superior do arquivo que faz referência a [ `System.ComponentModel.DataAnnotations` ](https://msdn.microsoft.com/en-us/library/system.componentmodel.dataannotations.aspx) namespace:</span><span class="sxs-lookup"><span data-stu-id="5b1dc-127">Add a `Imports` statement at the top of the file that references the [`System.ComponentModel.DataAnnotations`](https://msdn.microsoft.com/en-us/library/system.componentmodel.dataannotations.aspx) namespace:</span></span>

[!code-vb[Main](adding-validation-to-the-model/samples/sample1.vb)]

<span data-ttu-id="5b1dc-128">O namespace é parte do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-128">The namespace is part of the .NET Framework.</span></span> <span data-ttu-id="5b1dc-129">Ele fornece um conjunto interno de atributos de validação que você pode aplicar declarativamente para qualquer classe ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-129">It provides a built-in set of validation attributes that you can apply declaratively to any class or property.</span></span>

<span data-ttu-id="5b1dc-130">Atualizar agora o `Movie` classe para aproveitar o interno [ `Required` ](https://msdn.microsoft.com/en-us/library/system.componentmodel.dataannotations.requiredattribute.aspx), [ `StringLength` ](https://msdn.microsoft.com/en-us/library/system.componentmodel.dataannotations.stringlengthattribute.aspx), e [ `Range` ](https://msdn.microsoft.com/en-us/library/system.componentmodel.dataannotations.rangeattribute.aspx) atributos de validação .</span><span class="sxs-lookup"><span data-stu-id="5b1dc-130">Now update the `Movie` class to take advantage of the built-in [`Required`](https://msdn.microsoft.com/en-us/library/system.componentmodel.dataannotations.requiredattribute.aspx), [`StringLength`](https://msdn.microsoft.com/en-us/library/system.componentmodel.dataannotations.stringlengthattribute.aspx), and [`Range`](https://msdn.microsoft.com/en-us/library/system.componentmodel.dataannotations.rangeattribute.aspx) validation attributes.</span></span> <span data-ttu-id="5b1dc-131">Use o código a seguir como um exemplo de onde aplicar os atributos.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-131">Use the following code as an example of where to apply the attributes.</span></span>

[!code-vb[Main](adding-validation-to-the-model/samples/sample2.vb)]

<span data-ttu-id="5b1dc-132">Os atributos de validação especificam o comportamento que você deseja impor nas propriedades de modelo às quais eles são aplicados.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-132">The validation attributes specify behavior that you want to enforce on the model properties they are applied to.</span></span> <span data-ttu-id="5b1dc-133">O `Required` atributo indica que uma propriedade deve ter um valor; nesse exemplo, um filme deve ter valores para o `Title`, `ReleaseDate`, `Genre`, e `Price` propriedades para serem válidas.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-133">The `Required` attribute indicates that a property must have a value; in this sample, a movie has to have values for the `Title`, `ReleaseDate`, `Genre`, and `Price` properties in order to be valid.</span></span> <span data-ttu-id="5b1dc-134">O atributo `Range` restringe um valor a um intervalo especificado.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-134">The `Range` attribute constrains a value to within a specified range.</span></span> <span data-ttu-id="5b1dc-135">O atributo `StringLength` permite definir o tamanho máximo de uma propriedade de cadeia de caracteres e, opcionalmente, seu tamanho mínimo.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-135">The `StringLength` attribute lets you set the maximum length of a string property, and optionally its minimum length.</span></span>

<span data-ttu-id="5b1dc-136">Código primeiro assegura que as regras de validação que você especificar em uma classe de modelo são aplicadas antes que o aplicativo salva as alterações no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-136">Code First ensures that the validation rules you specify on a model class are enforced before the application saves changes in the database.</span></span> <span data-ttu-id="5b1dc-137">Por exemplo, o código a seguir lançará uma exceção quando o `SaveChanges` método é chamado, porque vários necessário `Movie` estiverem faltando valores de propriedade e o preço é zero (que está fora do intervalo válido).</span><span class="sxs-lookup"><span data-stu-id="5b1dc-137">For example, the code below will throw an exception when the `SaveChanges` method is called, because several required `Movie` property values are missing and the price is zero (which is out of the valid range).</span></span>

[!code-vb[Main](adding-validation-to-the-model/samples/sample3.vb)]

<span data-ttu-id="5b1dc-138">Com as regras de validação automaticamente impostas pelo .NET Framework ajuda a tornar o seu aplicativo mais robusto.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-138">Having validation rules automatically enforced by the .NET Framework helps make your application more robust.</span></span> <span data-ttu-id="5b1dc-139">Também garante que você não se esqueça de validar algo e inadvertidamente permita dados incorretos no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-139">It also ensures that you can't forget to validate something and inadvertently let bad data into the database.</span></span>

<span data-ttu-id="5b1dc-140">Aqui está um listagem para a atualização de códigos completa *Movie.vb* arquivo:</span><span class="sxs-lookup"><span data-stu-id="5b1dc-140">Here's a complete code listing for the updated *Movie.vb* file:</span></span>

[!code-vb[Main](adding-validation-to-the-model/samples/sample4.vb)]

## <a name="validation-error-ui-in-aspnet-mvc"></a><span data-ttu-id="5b1dc-141">Erro de validação de interface do usuário no ASP.NET MVC</span><span class="sxs-lookup"><span data-stu-id="5b1dc-141">Validation Error UI in ASP.NET MVC</span></span>

<span data-ttu-id="5b1dc-142">Execute novamente o aplicativo e navegue até o */Movies* URL.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-142">Re-run the application and navigate to the */Movies* URL.</span></span>

<span data-ttu-id="5b1dc-143">Clique o **criar filme** link para adicionar um novo filme.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-143">Click the **Create Movie** link to add a new movie.</span></span> <span data-ttu-id="5b1dc-144">Preencha o formulário com alguns valores inválidos e, em seguida, clique no **criar** botão.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-144">Fill out the form with some invalid values and then click the **Create** button.</span></span>

<span data-ttu-id="5b1dc-145">[![8_validationErrors](adding-validation-to-the-model/_static/image2.png)](adding-validation-to-the-model/_static/image1.png)</span><span class="sxs-lookup"><span data-stu-id="5b1dc-145">[![8_validationErrors](adding-validation-to-the-model/_static/image2.png)](adding-validation-to-the-model/_static/image1.png)</span></span>

<span data-ttu-id="5b1dc-146">Observe como o formulário automaticamente tem usado uma cor de plano de fundo para realçar as caixas de texto que contêm dados inválidos e emitida uma mensagem de erro de validação apropriadas ao lado de cada um.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-146">Notice how the form has automatically used a background color to highlight the text boxes that contain invalid data and has emitted an appropriate validation error message next to each one.</span></span> <span data-ttu-id="5b1dc-147">As mensagens de erro correspondem as cadeias de caracteres de erro especificado quando você anotado o `Movie` classe.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-147">The error messages match the error strings you specified when you annotated the `Movie` class.</span></span> <span data-ttu-id="5b1dc-148">Os erros são impostos no lado do cliente (usando JavaScript) e do lado do servidor (no caso de um usuário tiver JavaScript desabilitado).</span><span class="sxs-lookup"><span data-stu-id="5b1dc-148">The errors are enforced both client-side (using JavaScript) and server-side (in case a user has JavaScript disabled).</span></span>

<span data-ttu-id="5b1dc-149">Um benefício real é que você não precisa alterar uma única linha de código no `MoviesController` classe ou o *Create.vbhtml* exibição para permitir que essa validação da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-149">A real benefit is that you didn't need to change a single line of code in the `MoviesController` class or in the *Create.vbhtml* view in order to enable this validation UI.</span></span> <span data-ttu-id="5b1dc-150">O controlador e os modos de exibição que você criou anteriormente neste tutorial automaticamente escolhido até que a validação de regras que você especificou usando atributos no `Movie` classe de modelo.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-150">The controller and views you created earlier in this tutorial automatically picked up the validation rules that you specified using attributes on the `Movie` model class.</span></span>

## <a name="how-validation-occurs-in-the-create-view-and-create-action-method"></a><span data-ttu-id="5b1dc-151">Como a validação ocorre em criar exibir e cria o método de ação</span><span class="sxs-lookup"><span data-stu-id="5b1dc-151">How Validation Occurs in the Create View and Create Action Method</span></span>

<span data-ttu-id="5b1dc-152">Talvez você esteja se perguntando como a interface do usuário de validação foi gerada sem atualizações do código no controlador ou nas exibições.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-152">You might wonder how the validation UI was generated without any updates to the code in the controller or views.</span></span> <span data-ttu-id="5b1dc-153">A lista seguinte mostra o que o `Create` métodos de `MovieController` a aparência de classe.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-153">The next listing shows what the `Create` methods in the `MovieController` class look like.</span></span> <span data-ttu-id="5b1dc-154">Eles são inalterados desde como são criados anteriormente neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-154">They're unchanged from how you created them earlier in this tutorial.</span></span>

[!code-vb[Main](adding-validation-to-the-model/samples/sample5.vb)]

<span data-ttu-id="5b1dc-155">O primeiro método de ação exibe o formulário de criação inicial.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-155">The first action method displays the initial Create form.</span></span> <span data-ttu-id="5b1dc-156">O segundo manipula a postagem de formulário.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-156">The second handles the form post.</span></span> <span data-ttu-id="5b1dc-157">A segunda `Create` chamadas de método `ModelState.IsValid` para verificar se o filme tem erros de validação.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-157">The second `Create` method calls `ModelState.IsValid` to check whether the movie has any validation errors.</span></span> <span data-ttu-id="5b1dc-158">A chamada a esse método avalia os atributos de validação que foram aplicados ao objeto.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-158">Calling this method evaluates any validation attributes that have been applied to the object.</span></span> <span data-ttu-id="5b1dc-159">Se o objeto tem erros de validação, o `Create` método exibe novamente o formulário.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-159">If the object has validation errors, the `Create` method redisplays the form.</span></span> <span data-ttu-id="5b1dc-160">Se não houver erros, o método salvará o novo filme no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-160">If there are no errors, the method saves the new movie in the database.</span></span>

<span data-ttu-id="5b1dc-161">Abaixo está o *Create.vbhtml* exibir modelo Scaffold anteriormente no tutorial.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-161">Below is the *Create.vbhtml* view template that you scaffolded earlier in the tutorial.</span></span> <span data-ttu-id="5b1dc-162">Ela é usada pelos métodos de ação mostrados acima para exibir o formulário inicial e exibi-lo novamente em caso de erro.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-162">It's used by the action methods shown above both to display the initial form and to redisplay it in the event of an error.</span></span>

[!code-vbhtml[Main](adding-validation-to-the-model/samples/sample6.vbhtml)]

<span data-ttu-id="5b1dc-163">Observe como o código usa um `Html.EditorFor` auxiliar para gerar o `<input>` elemento para cada `Movie` propriedade.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-163">Notice how the code uses an `Html.EditorFor` helper to output the `<input>` element for each `Movie` property.</span></span> <span data-ttu-id="5b1dc-164">Ao lado deste auxiliar é uma chamada para o `Html.ValidationMessageFor` método auxiliar.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-164">Next to this helper is a call to the `Html.ValidationMessageFor` helper method.</span></span> <span data-ttu-id="5b1dc-165">Esses dois métodos auxiliares trabalham com o objeto de modelo que é passado pelo controlador para o modo de exibição (nesse caso, um `Movie` objeto).</span><span class="sxs-lookup"><span data-stu-id="5b1dc-165">These two helper methods work with the model object that's passed by the controller to the view (in this case, a `Movie` object).</span></span> <span data-ttu-id="5b1dc-166">Ele procuram automaticamente para atributos de validação especificados nos modelo e exibir mensagens de erro conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-166">They automatically look for validation attributes specified on the model and display error messages as appropriate.</span></span>

<span data-ttu-id="5b1dc-167">O que é realmente interessante sobre essa abordagem é que o controlador, nem o modelo de exibição criar sabe nada sobre as regras de validação real que está sendo impostas ou as mensagens de erro específico.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-167">What's really nice about this approach is that neither the controller nor the Create view template knows anything about the actual validation rules being enforced or about the specific error messages displayed.</span></span> <span data-ttu-id="5b1dc-168">As regras de validação e as cadeias de caracteres de erro são especificadas somente na classe `Movie`.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-168">The validation rules and the error strings are specified only in the `Movie` class.</span></span>

<span data-ttu-id="5b1dc-169">Se você quiser alterar a lógica de validação mais tarde, você pode fazer isso em exatamente um único local.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-169">If you want to change the validation logic later, you can do so in exactly one place.</span></span> <span data-ttu-id="5b1dc-170">Você não precisa se preocupar se diferentes partes do aplicativo estão inconsistentes com a forma como as regras são impostas – toda a lógica de validação será definida em um lugar e usada em todos os lugares.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-170">You won't have to worry about different parts of the application being inconsistent with how the rules are enforced — all validation logic will be defined in one place and used everywhere.</span></span> <span data-ttu-id="5b1dc-171">Isso mantém o código muito limpo e torna-o mais fácil de manter e desenvolver.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-171">This keeps the code very clean, and makes it easy to maintain and evolve.</span></span> <span data-ttu-id="5b1dc-172">E significa que você estará totalmente para respeitar o princípio seco.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-172">And it means that that you'll be fully honoring the DRY principle.</span></span>

## <a name="adding-formatting-to-the-movie-model"></a><span data-ttu-id="5b1dc-173">Adicionando formatação para o modelo de filme</span><span class="sxs-lookup"><span data-stu-id="5b1dc-173">Adding Formatting to the Movie Model</span></span>

<span data-ttu-id="5b1dc-174">Abra o *Movie.vb* arquivo.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-174">Open the *Movie.vb* file.</span></span> <span data-ttu-id="5b1dc-175">O [ `System.ComponentModel.DataAnnotations` ](https://msdn.microsoft.com/en-us/library/system.componentmodel.dataannotations.aspx) namespace fornece os atributos de formatação além do conjunto interno de atributos de validação.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-175">The [`System.ComponentModel.DataAnnotations`](https://msdn.microsoft.com/en-us/library/system.componentmodel.dataannotations.aspx) namespace provides formatting attributes in addition to the built-in set of validation attributes.</span></span> <span data-ttu-id="5b1dc-176">Você aplicará a [ `DisplayFormat` ](https://msdn.microsoft.com/en-us/library/system.componentmodel.dataannotations.displayformatattribute.aspx) atributo e um [ `DataType` ](https://msdn.microsoft.com/en-us/library/system.componentmodel.dataannotations.datatype.aspx) valor de enumeração para a data de lançamento e os campos de preço.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-176">You'll apply the [`DisplayFormat`](https://msdn.microsoft.com/en-us/library/system.componentmodel.dataannotations.displayformatattribute.aspx) attribute and a [`DataType`](https://msdn.microsoft.com/en-us/library/system.componentmodel.dataannotations.datatype.aspx) enumeration value to the release date and to the price fields.</span></span> <span data-ttu-id="5b1dc-177">O código a seguir mostra o `ReleaseDate` e `Price` propriedades com apropriada [ `DisplayFormat` ](https://msdn.microsoft.com/en-us/library/system.componentmodel.dataannotations.displayformatattribute.aspx) atributo.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-177">The following code shows the `ReleaseDate` and `Price` properties with the appropriate [`DisplayFormat`](https://msdn.microsoft.com/en-us/library/system.componentmodel.dataannotations.displayformatattribute.aspx) attribute.</span></span>

[!code-vb[Main](adding-validation-to-the-model/samples/sample7.vb)]

<span data-ttu-id="5b1dc-178">Como alternativa, você pode definir explicitamente um [ `DataFormatString` ](https://msdn.microsoft.com/en-us/library/system.string.format.aspx) valor.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-178">Alternatively, you could explicitly set a [`DataFormatString`](https://msdn.microsoft.com/en-us/library/system.string.format.aspx) value.</span></span> <span data-ttu-id="5b1dc-179">O código a seguir mostra a propriedade data de liberação com uma cadeia de caracteres de formato de data (isto é, "d").</span><span class="sxs-lookup"><span data-stu-id="5b1dc-179">The following code shows the release date property with a date format string (namely, "d").</span></span> <span data-ttu-id="5b1dc-180">Você usaria isso para especificar que você não deseja tempo como parte da data de lançamento.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-180">You'd use this to specify that you don't want to time as part of the release date.</span></span>

[!code-vb[Main](adding-validation-to-the-model/samples/sample8.vb)]

<span data-ttu-id="5b1dc-181">O código a seguir formatos de `Price` propriedade como moeda.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-181">The following code formats the `Price` property as currency.</span></span>

[!code-vb[Main](adding-validation-to-the-model/samples/sample9.vb)]

<span data-ttu-id="5b1dc-182">Completo `Movie` é mostrada abaixo.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-182">The complete `Movie` class is shown below.</span></span>

[!code-vb[Main](adding-validation-to-the-model/samples/sample10.vb)]

<span data-ttu-id="5b1dc-183">Execute o aplicativo e navegue até o `Movies` controlador.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-183">Run the application and browse to the `Movies` controller.</span></span>

![8_format_SM](adding-validation-to-the-model/_static/image3.png)

<span data-ttu-id="5b1dc-185">A próxima parte da série, vamos examinar o aplicativo e fazer algumas melhorias no gerado automaticamente `Details` e `Delete` métodos.</span><span class="sxs-lookup"><span data-stu-id="5b1dc-185">In the next part of the series, we'll review the application and make some improvements to the automatically generated `Details` and `Delete` methods..</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="5b1dc-186">[Anterior](adding-a-new-field.md)
[Próximo](improving-the-details-and-delete-methods.md)</span><span class="sxs-lookup"><span data-stu-id="5b1dc-186">[Previous](adding-a-new-field.md)
[Next](improving-the-details-and-delete-methods.md)</span></span>