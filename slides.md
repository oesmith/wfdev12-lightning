# Olly's Lightning Talk

!SLIDE

# Developers

## raise your hands

!SLIDE

![Y U NO?](images/yuno.jpg)

# Y U NO SPEC JS?

## olly.smith@wildfireapp.com

!SLIDE big-code

@@@ ruby
  # lightning-talk.feature
  In order to deliver awesome stuff
  As a developer who cares about his code working
  I want to be able to test my frontend javascript
@@@

!SLIDE

# Mocha.js

## visionmedia.github.com/mocha

A test runner that uses familiar BDD "describe" and "it" grammar.

@@@ javascript
describe('Array', function() {
  describe('#indexOf()', function() {
    it('should return -1 when the value is not present', function() {
      assert.equal(-1, [1,2,3].indexOf(5));
      assert.equal(-1, [1,2,3].indexOf(0));
    })
  })
})
@@@

!SLIDE

# Chai

## chaijs.com

A TDD/BDD assertion library.

@@@ javascript
// should
foo.should.be.a('string');
foo.should.equal('bar');
foo.should.have.length(3);
tea.should.have.property('flavors').with.length(3);

// expect
expect(foo).to.be.a('string');
expect(foo).to.equal('bar');
expect(foo).to.have.length(3);
expect(tea).to.have.property('flavors').with.length(3);
@@@

!SLIDE

# Chai-jQuery

## github.com/chaijs/chai-jquery

An extension to Chai that provides a bunch of jQuery-specific assertions.

@@@ javascript
$('#header').should.have.class('foo');
expect($('.year')).to.be.hidden;
$('.checked').should.be.checked;
@@@

!SLIDE

# Sinon.js

## sinonjs.org

Test spies, stubs and mocks.

@@@ javascript
describe('PubSub', function () {
  it("should call all subscribers", function () {
    var stub1 = sinon.stub(),
        stub2 = sinon.stub();
    
    PubSub.subscribe("message", stub1);
    PubSub.subscribe("message", stub2);

    PubSub.publishSync("message", undefined);

    expect(stub1.called).to.be.true;
    expect(stub2.called).to.be.true;
  })
})
@@@

!SLIDE

# Sinon.js

## (cont.)

Fake timers -- easily test timed methods!

@@@ javascript
describe('Image fader', function () {
  it('should fade the image in linearly over 500ms', function () {
    var clock = sinon.useFakeTimers();
    
    $('#img').animate({ opacity: 1.0 });

    clock.tick(250);
    expect($('#img').css('opacity')).to.equal(0.5);

    clock.tick(250);
    expect($('#img').css('opacity')).to.equal(1.0);
  });
})
@@@

!SLIDE

# Sinon.js

## (cont.)

Fake servers -- easily test remote API calls!

@@@ javascript
describe('Facebook client app', function () {

  it('should handle 500s', function () {

    var server = sinon.fakeServer.create(),
        success = sinon.stub(),
        error = sinon.stub();

    server.respondWith(
      "GET",
      "https://graph.facebook.com/me/accounts",
      [500, {}, 'Internal server error']
    );
    
    myFacebookAPI.getAccounts(success, error);
    
    server.respond();
    
    expect(success.called).to.be.false;
    expect(error.called).to.be.true;

  })

})
@@@

!SLIDE

# Konacha

## github.com/jfirebaugh/konacha

Hooks mocha+chai tests into your rails app.

Runs tests using capybara+selenium/webkit.

@@@

$ rake konacha:run
.........

Finished in 5.74 seconds
9 examples, 0 failures
@@@

!SLIDE

# Konacha

## (cont)

Uses the asset pipeline, so you can use sprockets to include your JS assets!

@@@ javascript
//= require that/thing

describe('something', function () {

  it('should do some stuff', function () {
    // ...
  })

})
@@@

!SLIDE

# Konacha

## (cont)

You can even write your tests in CoffeeScript! AMAZEBALLS!

@@@ coffeescript
#= require application

describe 'something', ->

  it 'should do some stuff', ->

    # ...


@@@

!SLIDE

# FIN

## (go test ALL THE THINGS!)

