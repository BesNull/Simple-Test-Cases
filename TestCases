import static io.restassured.RestAssured.given;
import io.restassured.builder.RequestSpecBuilder;
import io.restassured.http.ContentType;
import io.restassured.specification.RequestSpecification;
import static org.hamcrest.Matchers.*;
import org.junit.jupiter.api.Test;

public class RestTest {
    private static final RequestSpecification Test_Base = new RequestSpecBuilder()
            .setBaseUri("https://jsonplaceholder.typicode.com")
            .setBasePath("/posts")
            .setContentType(ContentType.JSON)
            .build();
    
    @Test
    public void testAllPosts(){ //здесь получаем массивы из значений полей Json 
        given()
                .spec(Test_Base)
                //.param("userId", "101")
                .when().get()  //"/list.json"
                .then()
                .statusCode(200)
                .body("$", hasSize(100))
                .header("Content-Type", equalTo("application/json; charset=utf-8"))
                .header("Server", equalTo("cloudflare"))
                .header("Content-Encoding", equalTo("gzip"))
                .body("id[0]", equalTo(1));
    }
      
    public void testById(){ //
        given()
                  .baseUri("https://jsonplaceholder.typicode.com")
                  .basePath("/posts/1")
                  .contentType(ContentType.JSON)
                  .when().get()
                  .then()
                  .statusCode(200)
                  .header("Content-Type", equalTo("application/json; charset=utf-8"))
                  .header("Server", equalTo("cloudflare"))
                  .header("Content-Encoding", equalTo("gzip"))
                  .body("id", equalTo(1))
                  .body("title",equalTo("sunt aut facere repellat provident occaecati excepturi optio reprehenderit"))
                  .body("body", equalTo("quia et suscipit\n"
                          + "suscipit recusandae consequuntur expedita et cum\n"
                          + "reprehenderit molestiae ut ut quas totam\n"
                          + "nostrum rerum est autem sunt rem eveniet architecto"))
                  .body("userId", equalTo(1));
                  // .body("size()", is(2));
      }
      
    public void testByQueryParametres(){ //здесь получаем массивы из значений полей Json 
        given()
                .spec(Test_Base)
                .param("userId", "1")
                .param("title", "qui est esse")
                .when().get()  
                .then()
                .statusCode(200)
                .header("Content-Type", equalTo("application/json; charset=utf-8"))
                .header("Server", equalTo("cloudflare"))
                .header("Content-Encoding", equalTo("gzip"))
                .body("body[0]", equalTo("est rerum tempore vitae\nsequi sint nihil reprehenderit dolor beatae ea dolores neque\nfugiat blanditiis voluptate porro vel nihil molestiae ut reiciendis\nqui aperiam non debitis possimus qui neque nisi nulla"))
                .body("id[0]", equalTo(2));
    }
}
