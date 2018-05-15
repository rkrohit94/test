# test
var expect = require('chai').expect
var Car = require('../car_class');

describe('Car', function() {

 describe("#fill", function() {
   it("gives the car petrol", function() {
     var car = new Car();
     expect(car.gallons).to.equal(0);
     car.fill(5);
     expect(car.gallons).to.equal(5);
     car.fill(6);
     expect(car.gallons).to.equal(11);
   });


  it("stores petrol per instance", function() {
     var car = new Car();
     car.fill(5);
     var car2 = new Car();
     car2.fill(4);
     expect(car.gallons).to.equal(5);
     expect(car2.gallons).to.equal(4);
    });

 it("uses petrol when driving", function() {
   var car = new Car(10);
   car.fill(10);
   expect(car.gallons).to.equal(10);
   car.drive(50);
   expect(car.gallons).to.equal(5);
   car.drive(50);
   expect(car.gallons).to.equal(0);
  });


 it("increments the odometer when driving", function() {
   var car = new Car();
   expect(car.odometer()).to.equal(0);
   car.drive(50);
   expect(car.odometer()).to.equal(50);
   car.drive(25);
   expect(car.odometer()).to.equal(75);
  });



 it("records trips", function() {
   var car = new Car(10);
   expect(car.trips()).to.eql([]);
   car.drive(50);
   expect(car.trips()).to.eql([
     '50 miles'
   ]);
   // car.drive(25);
   // car.drive(30);
   // expect(car.trips()).to.eql([
   //   '50 miles',
   //   '25 miles',
   //   '30 miles',
   // ]);
   });
 });
});

const expect = require('chai').expect;
const Passenger = require('../model/passenger');
const Bus = require('../model/bus');

describe('Bus', function () {

  it("gets initialized with a capacity", function () {
    var bus = new Bus(13);
    expect(bus.capacity).to.equal(13); 
    expect((new Bus(20)).capacity).to.equal(20); 
  }); 

  it(" bus starts out with vacancies equal to the capacity", function () {
    var bus1 = new Bus(12); 
    expect(bus1.vacancies()).to.equal(12); 

    var bus2 = new Bus(20); 
    expect(bus2.vacancies()).to.equal(20); 
  });

  it("allows you to board a passenger(id and name) with the fare paid", function () {
    var bus = new Bus(10);

    var joe = new Passenger(1, 'Joe Jones'); 
    var sue = new Passenger(2, 'Sue Summers');

    expect(joe.id).to.equal(1);
    expect(joe.name).to.equal('Joe Jones');
    expect(sue.id).to.equal(2);
    expect(sue.name).to.equal('Sue Summers');

    bus.board(joe, 4);
    expect(bus.vacancies()).to.equal(9);

    bus.board(sue, 3);
    expect(bus.vacancies()).to.equal(8);

    expect(bus.capacity).to.equal(10);
  });










  
  // it("allows you to see full names of passenger names/ids (in the order they were added)", function () {
  //   var bus = new Bus(5);
  //   var joe = new Passenger(1, 'Joe Jones');
  //   var sue = new Passenger(2, 'Sue Summers');

  //   expect(bus.passengerNames()).to.deep.equal([]);
    
  //   bus.board(joe, 4);
  //   expect(bus.passengerNames()).to.deep.equal(['Joe Jones (1)']);

  //   bus.board(sue, 3);
  //   expect(bus.passengerNames()).to.deep.equal(['Joe Jones (1)', 'Sue Summers (2)']);
  // });


  // it("allows passengers to switch seats", function () {
  //   var bus = new Bus(4);

  //   var joe = new Passenger(1, 'Joe Jones');
  //   var kat = new Passenger(4, 'Kat Kaplan');
  //   var sue = new Passenger(3, 'Sue Summers');
  //   var yas = new Passenger(2, 'Yasamine Yarrow');

  //   bus.board(joe);
  //   bus.board(kat);
  //   bus.board(sue);
  //   bus.board(yas);

  //   bus.switchSeats(joe, sue);
  //   expect(bus.passengerNames()).to.deep.equal([
  //     'Sue Summers (3)',
  //     'Kat Kaplan (4)',
  //     'Joe Jones (1)',
  //     'Yasamine Yarrow (2)',
  //   ]);

  //   bus.switchSeats(kat, joe);
  //   expect(bus.passengerNames()).to.deep.equal([
  //     'Sue Summers (3)',
  //     'Joe Jones (1)',
  //     'Kat Kaplan (4)',
  //     'Yasamine Yarrow (2)',
  //   ]);
  // });



  // it("allows you to get the total of all paid fares", function () {
  //   var bus = new Bus(10);

  //   var joe = new Passenger(1, 'Joe Jones');
  //   var sue = new Passenger(2, 'Sue Summers');
  //   var sally = new Passenger(3, 'Sally Sue ');

  //   bus.board(joe, 4);
  //   expect(bus.paidFares()).to.equal(4);

  //   bus.board(sue, 3);
  //   expect(bus.paidFares()).to.equal(7);

  //   bus.board(sally, 3)
  //   expect(bus.paidFares()).to.equal(10);
  // });



});
