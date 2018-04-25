# SpringAnnotationSelfLearning

Pure Java Spring Configuration
> You actually dont need XML to config Spring my dude
> There are 3 ways to configure a Spring Containter
	1) Full XML Config
	2) XML Component Scan
	3) Java Configuration > this is what we gonna learn
						  > zero xml here

	> How do boo?

		1 - Create a Java class and annotate as @Configuration
		2 - Add component scanning support: @ComponentScan

			@Configuration
			@ComponentScan("com.yazid.demo")
			public class doYouKnowDaWae {

			}

		3 - Reading Spring Java configuration class [from step 1]

			AnnotationConfigApplicationContext context =  new AnnotationConfigApplicationContext(DemoConfig.class);

		4 - Retrieve bean from Spring Container

			App myApp = demo.getBean("thisApp", App.class);

Defining Beans with Pure Java Codes
	1) Define method to expose bean:

		@Configuration
		public class SportConfig {

		@Bean //we define each bean invdividually
		public Coach swimCoach(){
			SwimCoach mySwimCoach = new SwimCoach();
		}
	}

	2) Inject bean dependencies:
		> swimCoach and happyFortuneService becomes the Bean ID

		@Configuration
		public class SportConfig {

		@Bean
		public FortuneService happyFortuneService(){
			return new HappyFortuneService;
			//creates new instance of HappyFourtuneService()
		}

		@Bean
		public Coach swimCoach(FortuneService fortuneService){
			SwimCoach mySwimCoach = new SwimCoach(happyFortuneService);
		}
	}

	3) Read Spring Java Config class (done up there)

		AnnotationConfigApplicationContext context =  new AnnotationConfigApplicationContext(DemoConfig.class);

	4) Retrieve bean from Spring container:

		Coach theCoach = context.getBean("swimCoach", Coach.class)
