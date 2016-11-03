# plugin-fangoly-spring-web-mvc-configurer
Load json configuration file, and setup a spring WebMvcConfigurer to control CROS.

Hi everyone:
I use this plugin with Spring Boot, to make a WebMvcConfigurer bean can load an outside json config file like this to control CORS(Cross-Origin Resource Sharing) feature in Spring MVC.

/resources/config_specific/springMvcWebConfig.json

/* The configuraton of CORS(Cross-Origin Resource Sharing).
 * configuration file for: plugin-fangoly-spring-web-mvc-configurer
 */
[
	{
		/* CORS mapping */
		mapping: "/hotels/*.json",
		/* allowed origins, string array */
		allowedOrigins: [],
		/* allowed credentials, boolean */
		allowCredentials: false,
		/* allowed headers, string array */
		allowedHeaders: [],
		/* allowed methods, string array */
		allowedMethods: [],
		/* exposed headers, string array */
		exposedHeaders: [],
		/* max age, long */
		maxAge: null
	}
]

And you can put this code in your spring configuration xml file to load the component FangolySpringMvnConfiguer.

<!-- spring mvc web configurer for CORS(Corss-Origin Resource Sharing) -->
<context:component-scan base-package="com.fanerp.fangoly.spring.mvc.config"></context:component-scan>

Or use annotations list this before a Configuration class definition.

@SpringBootApplication
@ComponentScan(basePackages={"com.fanerp.fangoly.spring.mvc.config"})
public class ConfigurationDef {

	...
}
