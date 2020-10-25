

###############################################################
# swagger api 示例注释
# 要把@OATEST 改为 @OA
###############################################################


###############################################################
# @OA\Info
###############################################################

/**
 * @OA\Info(
 *     description="This is a sample Petstore server.  You can find out more about Swagger at [http://swagger.io](http://swagger.io) or on [irc.freenode.net, #swagger](http://swagger.io/irc/).",
 *     version="1.0.0",
 *     title="Swagger Petstore",
 *     termsOfService="http://swagger.io/terms/",
 *     @OA\Contact(
 *         email="apiteam@swagger.io"
 *     ),
 *     @OA\License(
 *         name="Apache 2.0",
 *         url="http://www.apache.org/licenses/LICENSE-2.0.html"
 *     )
 * )
 */

###############################################################
# @OA\Tag
###############################################################

/**
 * @OA\Tag(
 *     name="pet",
 *     description="Everything about your Pets",
 *     @OA\ExternalDocumentation(
 *         description="Find out more",
 *         url="http://swagger.io"
 *     )
 * )
 * @OA\Tag(
 *     name="store",
 *     description="Access to Petstore orders",
 * )
 * @OA\Tag(
 *     name="user",
 *     description="Operations about user",
 *     @OA\ExternalDocumentation(
 *         description="Find out more about store",
 *         url="http://swagger.io"
 *     )
 * )
 */


###############################################################
# @OA\Server
###############################################################


/**
 * @OA\Server(
 *     description="SwaggerHUB API Mocking",
 *     url="https://virtserver.swaggerhub.com/swagger/Petstore/1.0.0"
 * )
 * @OA\ExternalDocumentation(
 *     description="Find out more about Swagger",
 *     url="http://swagger.io"
 * )
 */

###############################################################
# @OA\SecurityScheme
###############################################################

/**
 * @OA\SecurityScheme(
 *     type="oauth2",
 *     name="petstore_auth",
 *     securityScheme="petstore_auth",
 *     @OA\Flow(
 *         flow="implicit",
 *         authorizationUrl="http://petstore.swagger.io/oauth/dialog",
 *         scopes={
 *             "write:pets": "modify pets in your account",
 *             "read:pets": "read your pets",
 *         }
 *     )
 * )
 * @OA\SecurityScheme(
 *     type="apiKey",
 *     in="header",
 *     securityScheme="api_key",
 *     name="api_key"
 * )
 */

###############################################################
# @OA\Post
###############################################################
/**
 * @OA\Post(
 *     path="/pet",
 *     tags={"pet"},
 *     operationId="addPet",
 *     @OA\Response(
 *         response=405,
 *         description="Invalid input"
 *     ),
 *     security={
 *         {"petstore_auth": {"write:pets", "read:pets"}}
 *     },
 *     requestBody={"$ref": "#/components/requestBodies/Pet"}
 * )
 */

###############################################################
# @OA\Put
###############################################################
/**
 * @OA\Put(
 *     path="/pet",
 *     tags={"pet"},
 *     operationId="updatePet",
 *     @OA\Response(
 *         response=400,
 *         description="Invalid ID supplied"
 *     ),
 *     @OA\Response(
 *         response=404,
 *         description="Pet not found"
 *     ),
 *     @OA\Response(
 *         response=405,
 *         description="Validation exception"
 *     ),
 *     security={
 *         {"petstore_auth": {"write:pets", "read:pets"}}
 *     },
 *     requestBody={"$ref": "#/components/requestBodies/Pet"}
 * )
 */
###############################################################
# @OA\Get
###############################################################
/**
 * @OA\Get(
 *     path="/pet/findByStatus",
 *     tags={"pet"},
 *     summary="Finds Pets by status",
 *     description="Multiple status values can be provided with comma separated string",
 *     operationId="findPetsByStatus",
 *     deprecated=true,
 *     @OA\Parameter(
 *         name="status",
 *         in="query",
 *         description="Status values that needed to be considered for filter",
 *         required=true,
 *         explode=true,
 *         @OA\Schema(
 *             type="array",
 *             default="available",
 *             @OA\Items(
 *                 type="string",
 *                 enum = {"available", "pending", "sold"},
 *             )
 *         )
 *     ),
 *     @OA\Response(
 *         response=200,
 *         description="successful operation",
 *         @OA\JsonContent(
 *             type="array",
 *             @OA\Items(ref="#/components/schemas/Pet")
 *         ),
 *         @OA\XmlContent(
 *             type="array",
 *             @OA\Items(ref="#/components/schemas/Pet")
 *         )
 *     ),
 *     @OA\Response(
 *         response=400,
 *         description="Invalid status value"
 *     ),
 *     security={
 *         {"petstore_auth": {"write:pets", "read:pets"}}
 *     }
 * )
 */
###############################################################
# @OA\Get  byId
###############################################################
/**
 * @OA\Get(
 *     path="/pet/{petId}",
 *     tags={"pet"},
 *     summary="Find pet by ID",
 *     description="Returns a single pet",
 *     operationId="getPetById",
 *     @OA\Parameter(
 *         name="petId",
 *         in="path",
 *         description="ID of pet to return",
 *         required=true,
 *         @OA\Schema(
 *             type="integer",
 *             format="int64"
 *         )
 *     ),
 *     @OA\Response(
 *         response=200,
 *         description="successful operation",
 *         @OA\JsonContent(ref="#/components/schemas/Pet"),
 *         @OA\XmlContent(ref="#/components/schemas/Pet"),
 *     ),
 *     @OA\Response(
 *         response=400,
 *         description="Invalid ID supplier"
 *     ),
 *     @OA\Response(
 *         response=404,
 *         description="Pet not found"
 *     ),
 *     security={
 *         {"api_key": {}}
 *     }
 * )
 *
 * @param int $id
 */

###############################################################
# @OA\Delete
###############################################################
/**
 * @OA\Delete(
 *     path="/pet/{petId}",
 *     tags={"pet"},
 *     summary="Deletes a pet",
 *     operationId="deletePet",
 *     @OA\Parameter(
 *         name="api_key",
 *         in="header",
 *         required=false,
 *         @OA\Schema(
 *             type="string"
 *         )
 *     ),
 *     @OA\Parameter(
 *         name="petId",
 *         in="path",
 *         description="Pet id to delete",
 *         required=true,
 *         @OA\Schema(
 *             type="integer",
 *             format="int64"
 *         ),
 *     ),
 *     @OA\Response(
 *         response=400,
 *         description="Invalid ID supplied",
 *     ),
 *     @OA\Response(
 *         response=404,
 *         description="Pet not found",
 *     ),
 *     security={
 *         {"petstore_auth": {"write:pets", "read:pets"}}
 *     },
 * )
 */