# <a name="how-to-buildrun-secure-user-data-sample"></a><span data-ttu-id="fc172-101">Como exemplo de dados de usuário segura Compile/execute</span><span class="sxs-lookup"><span data-stu-id="fc172-101">How to build/run Secure user data sample</span></span>

* <span data-ttu-id="fc172-102">Definir a senha com a ferramenta Gerenciador de segredo:</span><span class="sxs-lookup"><span data-stu-id="fc172-102">Set password with the Secret Manager tool:</span></span>

  `dotnet user-secrets set SeedUserPW <pw>`

* <span data-ttu-id="fc172-103">Atualize o banco de dados:</span><span class="sxs-lookup"><span data-stu-id="fc172-103">Update the database:</span></span>

    `dotnet ef database update`

* <span data-ttu-id="fc172-104">Habilitar o SSL no projeto</span><span class="sxs-lookup"><span data-stu-id="fc172-104">Enable SSL in the project</span></span>