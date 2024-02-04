# RSpec
* RSpec is a testing tool in ruby, which is created for Behaviour Driven Development (BDD)
* It is a most frequently used testing library, as it is Domain Specific Language (DSL)
* Before BDD we have to understand TDD - Test Driven Development 

## TTD
TTD is a technique which we were writing the testing code before writing the actual working code
First we write the smallest possible test case 
Then we run the test  and watch it fails 
Then we write the code to make the test pass
Repeat the steps until all the test passes
Then refactor the code efficiently 

## RSpec is composed of multiple libraries, which are designed to work together, or can be used independently with other testing tools
* rspec-core: foundation of spec gem - base library that organises and run the tests - test runner
* rspec-expectations: This is used to describe the syntax to write the expectations and assertions which tells how the code has to work 
* rspec-mocks: It is used to fake the behaviour of the classes or objects - fake in the sense that the feature should be made independent which  is isolated.
    - eg. if there are three things, to test a thing this library fakes the other two to test this thing solely
* rspec-rails: gem integrates the rspec with the Ruby on Rails web framework

## TYPES OF TESTS
* Unit testing - small size of testing
* Integration testing - mid size testing
* End 2 End testing - entire level testing 

## UNIT TESTING 
- Testing a part of code isolated and independently which doesn’t depend on any other classes or objects or any other  part of code 
- Testing a single class, object, module, method
- These specs are easy to test and these are fast 

## E2E TESTING or ACCEPTANCE TEST
- End 2 End testing is the testing where we are testing the entire application from beginning to end   
- Focus on a feature and its interaction with entire system
- These specs are hard to write and run slow and brittle 
- Brittle in the sense that all the features were coupled any one change can break the system

## INTEGRATION TESTING
- It is in between the unit and e2e testing that neither we test as a unit isolated code nor we do e2e testing 
- In integration testing we are not testing entirely this is somewhere between unit and e2e testing 
- May be we can test a couple of classes which shall interact with each other 

## DESCRIBE Method
- Describe is a keyword that used to build a example group
- Example group is a construct that organises a specific related collection of tests
- In rspec a test is known as example an example of how something is supposed to work
- So an example group is a one or more examples/tests
  
RSpec.describe 'Card' do

end

## IT Method 
- It method is used inside the block of the describe method 
- It method should be used to describe about the funcitonality /behaviour
- We are not going to tell how the function is technically built we are just telling that what this function will do 
`RSpec.describe 'Card' do
 it 'has a type' do     
 end 
end`
In the above we are not saying that we are using a array or hashes, we are just saying that the cards having types (spade, hearts, etc)
- It should say the overall functionality/behaviour
- ‘It’ have an alias which means a another name called ’specify’

We can also write the code as
`RSpec.describe 'Card' do
 specify 'has a type' do     
 end 
end`
But ‘it’ is the  most commonly use method though specify is also same as it.


## Expect Method & EQ Method 
- Expect method is a method which accepts arguments and the arguments is which our spec is going to evaluate
- The thing spec going to evaluate is given as argument for the expect method 
- It can be an object or attribute of that object or it might be a normal ruby expression which like 2*3 
 
- EQ method is going to create a matcher which should the tests success /match
- Matcher is the heart of the expectation
- We can test for equality, inclusion, or an expression throws an error
- Here eq is used for equality which is ‘==‘

## RSpec.describe 'Card' do
 ``it 'has a type' do
  card = Card.new('Twos of Heart')   expect(card.type).to eq('Twos of Heart')
 end 
end``
- Here we are creating a it block which says that the card has type 
- The expect method is going to evaluate the type of card 
- Iit has the to method which checks the expect method with the eq method
- The type of card should be a string ’Two of Hearts’

We can also say that 
`expect(2*2).to eq(4)`

## RUNNING SPEC FILES

rspec	This command runs all the spec files
rspec spec/card_spec.rb	This command used run the specific spec file which the directory should be correct 

READING FAILURES
As we are implementing TDD so first we have to write the test and run it and make it to fail now we are going to run the code and get the error(RED)
Failures:

  1) Card card has type
     Failure/Error: card = Card.new('twos of heart')
     
    ` NoMethodError:
       undefined method `new' for nil:NilClass
     #./spec/card_spec.rb:3:in `block (2 levels) in <top (required)>'

Finished in 0.00504 seconds (files took 0.36669 seconds to load)
1 example, 1 failure

Failed examples:

rspec ./spec/card_spec.rb:2 # Card card has type
Now we got an error that there is an uninitilised class called Card
Each ‘it’ method creates one examples 

## WRITING THE CODE
Now we are going to write the code for which we have wrote the test, just by solving the failure raised above.
When we faced red now we have to code to get green 
And then we have to refactor the code again to make the code optimise this is a cycle.
