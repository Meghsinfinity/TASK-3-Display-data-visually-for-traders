# TASK-3-Display-data-visually-for-traders
import [ ServerRespond from/DataStreamer';

Row to be inserted to Perspective Table */

export interface Row [

stock: string.

top-ask-price: number,

timestamp: Date,

price_abe: number, //(ask bid) / 2

price_def: number,

ratio: number, // price ABC price DEF

timestamp: Date, // data timestamp for X axis

upper-bound: number, 0.05

lower bound number, // 0.05

trigger-alert: number | undefined.

export class DataManipulator {

static generateRow(serverResponde: ServerRespond||): Row[]

return serverResponds.map(fel: any) => {

return {

top_ask_price: el.top_ask && el.top_ask.price 11 0.

stock: el.stock.

timestamp: el.timestamp.

1:

})

static generateRow(serverRespond: ServerRespond[]): Row [

const priceABC (serverRespond101.top.ask.price

serverRespond[0].top_bid.price) 2:

const priceDEF (serverRespond[1].top.ask.price

server Respond[1].top_bid.price) /2:

const ratio priceABC priceDEF;

const upperBound 1 0.05:

const lower Bound 10.05:

return ( price abe: priceABC,

price def: priceDEF,

ratio,

timestamp: serverRespond[0].timestamp> serverRespond [1].timestamp?

serverRespond[0].timestamp serverRespond[1].timestamp.

upper bound: upper Bound,

lower bound: lower Bound.

trigger-alert: (ratio upperBound || ratio lowerBound) ratio: undefined.

1:

diff --git a/src/Graph.tax b/src/Graph.tsx

index 58fb997..54a6f1f 100644

a/src/Graph.tsx

+++ b/src/Graph.tsxX

60-23.30 23.40 class Graph extends Component<IProps, []> [ const elem document.getElementsByTagName('perspective-viewer')[0] as unknown

as PerspectiveViewer Element;
const schema [

stock: 'string'.

top_ask.price: 'float'.

top-bid price: 'float'.

price.abe: 'float'.

price.def: 'float'.

ratio: 'float',

timestamp: 'date'.

upper bound: 'float',

lower bound: 'float',

trigger.alert: 'float'.

1:

if (window.perspective && window.perspective.worker()) {

if (window.perspective) {

this.table window.perspective.worker().table (schema);

if (this.table) (

// Load the table in the <perspective-viewer> DOM reference.

elem.load(this.table);

elem.setAttribute('view', 'y-line');

elem.setAttribute('column-pivots", ["stock"]'); elem.setAttribute('row-pivots', ['timestamp"]");

elem.setAttribute('columns' ('top_ask_price*):

elem.setAttribute('columns'. (ratio", "lower bound", "upper bound",

trigger.alert']'); "

elem.setAttribute('aggregates'. JSON.stringify(f

stock: 'distinctcount'.

top_ask_price: 'avg'.

top_bid.price: 'avg'.

price_abc: avg.

price_def: 'avg'.

ratio: 'avg'.

timestamp: 'distinct count',

upper bound: 'avg',

lower bound: 'avg'.

trigger_alert: 'avg'.

31):

componentDidUpdate() E

if (this.table) (

this.table.update(

this.table.update([

DataManipulator.generateRow(this.props.datal.

):

10:

1

2.17.1
